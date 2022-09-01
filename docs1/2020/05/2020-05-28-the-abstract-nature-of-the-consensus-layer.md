# The abstract nature of the Cardano consensus layer
### **This new series of technical posts by IOHK's engineers considers the choices being made**
![](img/2020-05-28-the-abstract-nature-of-the-consensus-layer.002.png) 28 May 2020![](img/2020-05-28-the-abstract-nature-of-the-consensus-layer.002.png)[ Edsko de Vries](tmp//en/blog/authors/edsko-de-vries/page-1/)![](img/2020-05-28-the-abstract-nature-of-the-consensus-layer.003.png) 21 mins read

![Edsko de Vries](img/2020-05-28-the-abstract-nature-of-the-consensus-layer.004.png)[](tmp//en/blog/authors/edsko-de-vries/page-1/)
### [**Edsko de Vries**](tmp//en/blog/authors/edsko-de-vries/page-1/)
Software Engineer

Well-Typed

- ![](img/2020-05-28-the-abstract-nature-of-the-consensus-layer.005.png)[](http://www.linkedin.com/in/edsko-de-vries-04126b31 "LinkedIn")
- ![](img/2020-05-28-the-abstract-nature-of-the-consensus-layer.006.png)[](https://twitter.com/EdskoDeVries "Twitter")
- ![](img/2020-05-28-the-abstract-nature-of-the-consensus-layer.007.png)[](https://github.com/edsko "GitHub")

![The abstract nature of the Cardano consensus layer](img/2020-05-28-the-abstract-nature-of-the-consensus-layer.008.jpeg)

*As we head towards Shelley on the Cardano mainnet, weâ€™re keen to keep you up to date with the latest news. We also want to highlight the tireless work going on behind the scenes, and the team of engineers responsible.*

*In this Developer Deep Dive series of occasional technical blogs, we open the floor to IOHK's engineers. Over the months ahead, our Haskell developers will offer a candid glimpse into the core elements of the Cardano platform and protocols, and share insights into the choices that have been made.*

*Here, in the first of the series, we consider the use of abstraction in the consensus layer.*
## **Introduction**
The [Cardano consensus layer](https://github.com/input-output-hk/ouroboros-network/tree/master/ouroboros-consensus) has two important responsibilities:

- It runs the blockchain *consensus* protocol. In the context of a blockchain, consensus - that is, 'majority of opinion' - means everyone involved in running the blockchain agrees on what the one true chain is. This means that the consensus layer is in charge of adopting blocks, choosing between competing chains if there are any, and deciding when to produce blocks of its own.
- It is responsible for maintaining all the *state* required to make these decisions. To decide whether or not to adopt a block, the protocol needs to validate that block with respect to the *state of the ledger*. If it decides to switch to a different chain (a different tine of a fork in the chain), it must keep enough *history* to be able to reconstruct the ledger state on that chain. To be able to produce blocks, it must maintain a *mempool* of transactions to be inserted into those blocks.

The consensus layer mediates between the [network layer below it](https://github.com/input-output-hk/ouroboros-network/tree/master/ouroboros-network), which deals with concerns such as communication protocols and peer selection, and the [ledger layer above it](https://github.com/input-output-hk/cardano-ledger), which specifies what the state of the ledger looks like and how it must be updated with each new block. The ledger layer is entirely stateless, and consists exclusively of pure functions. In turn, the consensus layer does not need to know the exact nature of the ledger state, or indeed the contents of the blocks (apart from some header fields required to run the consensus protocol).

Extensive use is made of abstraction in the consensus layer. This is important for many reasons:

- It allows programmers to *inject failures* when running tests. For example, we abstract the [underlying file system](https://github.com/input-output-hk/ouroboros-network/blob/master/ouroboros-consensus/src/Ouroboros/Consensus/Storage/FS/API.hs), and use this to stress-test the storage layer while simulating all manner of disk faults. Similarly, we abstract over [time](https://github.com/input-output-hk/ouroboros-network/blob/master/io-sim-classes/src/Control/Monad/Class/MonadTime.hs), and use this to check what happens to a node when a user's system clock jumps forward or backwards.
- It allows us to *instantiate* the consensus layer with many different kinds of ledgers. Currently we use this to run the consensus layer with the Byron ledger (the ledger that's currently on the Cardano blockchain) as well as the Shelley ledger for the upcoming Shelley Haskell testnet. In addition, we use it to run the consensus layer with various kinds of ledgers specifically designed for testing, typically much simpler than 'real' ledgers, so that we can focus our tests on the consensus layer itself.
- It improves *compositionality*, allowing us to build larger components from smaller components. For example, the Shelley testnet ledger *only* contains the Shelley ledger, but once Shelley is released the real chain will contain the Byron ledger up to the hard fork point, and the Shelley ledger thereafter. This means we need a ledger layer that *switches* between two ledgers at a specific point. Rather than defining a new ledger, we can instead define a [hard fork combinator](https://github.com/input-output-hk/ouroboros-network/pull/1175) that implements precisely this, and only this, functionality. This improves reusability of the code (we will not need to reimplement hard fork functionality when the next hard fork comes around), as well as separation of concerns: the development and testing of the hard fork combinator does not depend on the specifics of the ledgers it switches between.
- Closely related to the last point, the use of abstraction improves *testability*. We can define combinators that define minor variations of consensus protocols that allow us to focus on specific aspects. For example, we have a combinator that takes an existing consensus protocol and overrides only the check whether we should produce a block. We can then use this to generate testing scenarios in which many nodes produce a block in a given slot or, conversely, no nodes at all, and verify that the consensus layer does the right thing under such circumstances. Without a combinator to override this aspect of the consensus layer, it would be left to chance whether such scenarios arise. Although we can control 'chance' in testing (by choosing a particular starting seed for the pseudorandom number generator), it would be impossible to set up specific scenarios, or indeed automatically shrink failing test cases to a minimal test case. With these testing consensus combinators, the test can literally just use a schedule specifying which nodes should produce blocks in which slots. We can then generate such schedules randomly, run them, and if there is a bug, shrink them to a minimal test case that still triggers the bug. Such a minimal failing schedule is *much* easier to debug, understand and work with than merely a choice of initial random seed that causes... *something*... to happen at... *some point*.

To achieve all of this, however, the consensus layer needs to make use of some sophisticated Haskell types. In this blog post we will develop a 'mini consensus protocol', explain exactly how we abstract various aspects, and how we can make use of those abstractions to define various combinators. The remainder of this blog post assumes that the reader is familiar with Haskell.
## **Preliminaries**
The Cardano consensus layer is designed to support the Ouroboros [family of consensus protocols](https://iohk.io/en/research/library/), all of which make a fundamental assumption that time is split into *slots*, where the blockchain can have at most one block per slot. In this article, we define a slot number to just be an Int:

type SlotNo = Int

We will also need a minimal model of public-key encryption, specifically

data PrivateKey

data PublicKey

data Signature

verifySig :: Signature -> PublicKey -> Bool

The only language extension we will need in this blog post is TypeFamilies, although the real implementation uses far more. If you want to follow along, [download the full source code](https://ucarecdn.com/ddbeb491-dd41-4deb-b112-c9ab6980c2b3/MiniConsensus.hs).
## **Consensus protocol**
As mentioned at the start of this post, the consensus protocol has three main responsibilities:

1. Leader check (should we produce a block?)
1. Chain selection
1. Block verification

The protocol is intended to be independent from a concrete choice of block, as well as a concrete choice of ledger, so that a single protocol can be run with different kinds of blocks and/or ledgers. Therefore, each of these three responsibilities defines its own 'view' on the data it requires.
### **Leader check**
The leader check runs at every slot, and must determine if the node should produce a block. In general, the leader check might require some information extracted from the ledger state:

type family LedgerView p :: \*

For example, in the [Ouroboros Praos](https://iohk.io/en/research/library/papers/ouroboros-praosan-adaptively-securesemi-synchronous-proof-of-stake-protocol/) consensus protocol that will initially power Shelley, a node's probability of being elected a leader (that is, be allowed produce a block) depends on its stake; the node's stake, of course, comes from the ledger state.
### **Chain selection**
'Chain selection' refers to the process of choosing between two competing chains. The main criterion here is chain length, but some protocols may have additional requirements. For example, blocks are typically signed by a 'hot' key that exists on the server, which in turn is generated by a 'cold' key that never exists on any networked device. When the hot key is compromised, the node operator can generate a new one from the cold key, and 'delegate' to that new key. So, in a choice between two chains of equal length, both of which have a tip signed by the same *cold* key but a different *hot* key, a consensus protocol will prefer the newer hot key. To allow specific consensus protocols to state requirements such as this, we therefore introduce a SelectView, specifying what information the protocol expects to be present in the block:

type family SelectView p :: \*
### **Header validation**
Block validation is mostly a ledger concern; checks such as verifying that all inputs to a transaction are available to avoid double-spending are defined in the ledger layer. The consensus layer is mostly unaware of what's inside the blocks; indeed, it might not even be a cryptocurrency, but a [different application of blockchain technology](https://bitcoinmagazine.com/articles/where-coffee-just-grows-connecting-ethiopian-agritech-blockchain).

Blocks (more precisely, block headers) also contain a few things specifically to support the consensus layer, however. To stick with the Praos example, Praos expects various cryptographic proofs to be present related to deriving entropy from the blockchain. Verifying these is the consensus layer's responsibility, and so we define a third and final view of the fields that consensus must validate:

type family ValidateView p :: \*
### **Protocol definition**
We need one more type family\*: each protocol might require some static information to run; keys to sign blocks, its own identity for the leader check, etc. We call this the 'node configuration', and define it as

data family NodeConfig p :: \*

We can now tie everything together in the abstract definition of a consensus protocol. The three methods of the class correspond to the three responsibilities we mentioned; each method is passed the static node configuration, as well the specific view required for that method. Note that p here is simply a type-level tag identifying a specific protocol; it never exists at the value level.

class ConsensusProtocol p where

`  `-- | Chain selection

`  `selectChain :: NodeConfig p -> SelectView p -> SelectView p -> Ordering

`  `-- | Header validation

`  `validateBlk :: NodeConfig p -> ValidateView p -> Bool

`  `-- | Leader check

`  `--

`  `-- NOTE: In the real implementation this is additionally parameterized over

`  `-- some kind of 'proof' that we are indeed the leader. We ignore that here.

`  `checkLeader :: NodeConfig p -> SlotNo -> LedgerView p -> Bool
### **Example: Permissive BFT (PBFT)**
Permissive BFT is a simple consensus protocol where nodes produce blocks according to a round robin schedule: first node A, then B, then C, then back to A. We call the index of a node in that schedule the 'NodeId'. This is a concept for PBFT only, not something the rest of the consensus layer needs to be aware of:

type NodeId = Int

The node configuration required by PBFT is the node's own identity, as well as the public keys of all nodes that can appear in the schedule:

data PBft -- The type level tag identifying this protocol

data instance NodeConfig PBft = CfgPBft {

`      `-- | The node's ID

`      `pbftId :: NodeId

`      `-- | The verification keys of all nodes

`    `, pbftKeys :: [PublicKey]

`    `}

Since PBFT is a simple round-robin schedule, it does not need any information from the ledger:

type instance LedgerView PBft = ()

Chain selection just looks at the chain length; for the sake of simplicity, we will assume here that longer chains will end on a larger slot number\*\*, and so chain selection just needs to know the slot number of the tip:

type instance SelectView PBft = SlotNo

Finally, when validating blocks, we must check that they are signed by any of the nodes that are allowed to produce blocks (that can appear in the schedule):

type instance ValidateView PBft = Signature

Defining the protocol is now simple:

instance ConsensusProtocol PBft where

`  `selectChain \_cfg         = compare

`  `validateHdr  cfg sig     = any (verifySig sig) (pbftKeys cfg)

`  `checkLeader  cfg slot () = slot `mod` length (pbftKeys cfg) == pbftId cfg

Chain selection just compares slot numbers; validation checks if the key is one of the allowed slot leaders, and leader selection does some modular arithmetic to determine if it's that node's turn.

Note that the round-robin schedule is used *only* in the check whether or not we are a leader; for historical blocks (that is, when doing validation), we merely check that the block was signed by *any* of the allowed leaders, not in which order. This is the 'permissive' part of PBFT; the [real implementation](https://github.com/input-output-hk/ouroboros-network/blob/master/ouroboros-consensus/src/Ouroboros/Consensus/Protocol/PBFT.hs) does do one additional check (that there isn't any single leader signing more than its share), which we omit from this blog post.
### **Protocol combinator example: explicit leader schedule**
As mentioned in the introduction, for testing it is useful to be able to explicitly decide the order in which nodes sign blocks. To do this, we can define a *protocol combinator* that takes a protocol and just overrides the is-leader check to check a fixed schedule instead:

data OverrideSchedule p -- As before, just a type-level tag

The configuration required to run such a protocol is the schedule and the node's ID within this schedule, in addition to whatever configuration the underlying protocol p requires:

data instance NodeConfig (OverrideSchedule p) = CfgOverride {

`      `-- | The explicit schedule of nodes to sign blocks

`      `schedule :: Map SlotNo [NodeId]

`      `-- | Our own identifier in the schedule

`      `-- (PBFT has such an identifier also, but many protocols don't)

`    `, scheduleId :: NodeId

`      `-- | Config of the underlying protocol

`    `, scheduleP :: NodeConfig p

`    `}

Chain selection is unchanged, and hence so is the view on blocks required for chain selection:

type instance SelectView (OverrideSchedule p) = SelectView p

However, we need to override header validation---indeed, disable it altogether---because if the underlying protocol *verifies* that the blocks are signed by the right node, then obviously such a check would be incompatible with this override. We therefore don't need anything from the block to validate it (since we don't *do* any validation):

type instance LedgerView (OverrideSchedule p) = ()

Defining the protocol is now trivial:

instance ConsensusProtocol p => ConsensusProtocol (OverrideSchedule p) where

`  `selectChain  cfg      = selectChain (scheduleP cfg)

`  `validateHdr \_cfg   () = True

`  `checkLeader  cfg s () = scheduleId cfg `elem` (schedule cfg) Map.! s

Chain selection just uses the chain selection of the underlying protocol p, block validation does nothing, and the is-leader check refers to the static schedule.
## **From blocks to protocols**
Just like the consensus protocol, a specific choice of block may also come with its own required configuration data:

data family BlockConfig b :: \*

Many blocks can use the same protocol, but a specific type of block is designed for a specific kind of protocol. We therefore introduce a type family mapping a block type to its associated protocol:

type family BlockProtocol b :: \*

We then say a block *supports its protocol* if we can construct the views on that block required by its specific protocol:

class BlockSupportsProtocol b where

`  `selectView   :: BlockConfig b -> b -> SelectView   (BlockProtocol b)

`  `validateView :: BlockConfig b -> b -> ValidateView (BlockProtocol b)
### **Example: (Simplified) Byron blocks**
Stripped to their bare bones, blocks on the Byron blockchain look something like

type Epoch   = Int

type RelSlot = Int

data ByronBlock = ByronBlock {

`      `bbSignature :: Signature

`    `, bbEpoch     :: Epoch

`    `, bbRelSlot   :: RelSlot

`    `}

We mentioned above that the Ouroboros consensus protocol family assumes that time is split into *slots*. In addition, they also assume that these slots are grouped into *epochs*. Byron blocks do not contain an absolute number, but instead an *epoch number* and a *relative* slot number within that epoch. The number of slots per epoch on the Byron chain is fixed at slightly over 10*k*, but for testing it is useful to be able to vary *k*, the security parameter, and so it is configurable; this is (part of) the configuration necessary to work with Byron blocks:

data instance BlockConfig ByronBlock = ByronConfig {

`      `bcEpochLen :: Int

`    `}

Given the Byron configuration, it is then a simple matter of converting the pair of an epoch number and a relative slot into an absolute slot number:

bbSlotNo :: BlockConfig ByronBlock -> ByronBlock -> SlotNo

bbSlotNo cfg blk = bbEpoch blk \* bcEpochLen cfg + bbRelSlot blk

What about the protocol? Well, the Byron chain runs PBFT, and so we can define

type instance BlockProtocol ByronBlock = PBft

Proving that the Byron block supports this protocol is easy:

instance BlockSupportsProtocol ByronBlock where

`  `selectView   = bbSlotNo

`  `validateView = const bbSignature
## **The ledger state**
The consensus layer not only runs the consensus protocol, it also manages the ledger state. It doesn't, however, care much what the ledger state looks like specifically; instead, it merely assumes that some type of ledger state is associated with a block type:

data family LedgerState b :: \*

We will need one additional type family. When we apply a block to the ledger state, we might get an error if the block is invalid. The specific type of ledger errors is defined in the ledger layer, and is, of course, highly ledger specific. For example, the Shelley ledger will have errors related to staking, whereas the Byron ledger does not, because it does not support staking; and ledgers that aren't cryptocurrencies will have very different kinds of errors.

data family LedgerError b :: \*

We now define two type classes. The first merely describes the interface to the ledger layer, saying that we must be able to apply a block to the ledger state and either get an error (if the block was invalid) or the updated ledger state:

class UpdateLedger b where

`  `applyBlk :: b -> LedgerState b -> Either (LedgerError b) (LedgerState b)

Second, we will define a type class that connects the ledger associated with a block to the consensus protocol associated with that block. Just like the BlockSupportsProtocol provides functionality to derive views from the block required by the consensus protocol, LedgerSupportsProtocol similarly provides functionality to derive views from the *ledger state* required by the consensus protocol:

class LedgerSupportsProtocol b where

`  `-- | Extract the relevant information from the ledger state

`  `ledgerView :: LedgerState b -> LedgerView (BlockProtocol b)

We will see in the next section why it is useful to separate the integration with the ledger (UpdateLedger) from its connection to the consensus protocol (LedgerSupportsProtocol).
### **Block combinators**
As a final example of the power of combinators, we will show that we can define a combinator on *blocks* and their associated ledgers. As an example of where this is useful, the Byron blockchain comes with an [implementation](https://github.com/input-output-hk/cardano-ledger) as well as an [executable specification](https://github.com/input-output-hk/cardano-ledger-specs/tree/master/byron). It is useful to instantiate the consensus layer with *both* of these ledgers, so we can verify that the implementation agrees with the specification at all points along the way. This means that blocks in this 'dual ledger' set-up are, in fact, a pair of blocks\*\*\*.

data DualBlock main aux = DualBlock {

`      `dbMain :: main

`    `, dbAux  :: aux

`    `}

The definition of the dual ledger state and dual ledger error are similar:

data instance LedgerState (DualBlock main aux) = DualLedger {

`      `dlMain :: LedgerState main

`    `, dlAux  :: LedgerState aux

`    `}

data instance LedgerError (DualBlock main aux) = DualError {

`      `deMain :: LedgerError main

`    `, deAux  :: LedgerError aux

`    `}

To apply a dual block to the dual ledger state, we simply apply each block to its associated state. This particular combinator assumes that the two ledgers must always agree whether or not a particular block is valid, which is suitable for comparing an implementation and a specification; other choices (other combinators) are also possible:

instance ( UpdateLedger main

`         `, UpdateLedger aux

`         `) => UpdateLedger (DualBlock main aux) where

`  `applyBlk (DualBlock  dbMain dbAux)

`           `(DualLedger dlMain dlAux) =

`    `case (applyBlk dbMain dlMain, applyBlk dbAux dlAux) of

`      `(Left  deMain  , Left  deAux ) -> Left  $ DualError  deMain  deAux

`      `(Right dlMain' , Right dlAux') -> Right $ DualLedger dlMain' dlAux'

`      `\_otherwise                     -> error "ledgers disagree"

Since the intention of the dual ledger is to compare two *ledger* implementations, it will suffice to have all *consensus* concerns be driven by the first ('main') block; we don't need an instance for ProtocolLedgerView for the auxiliary block, and, indeed, in general might not be able to give one. This means that the block protocol of the dual block is the block protocol of the main block:

type instance BlockProtocol (DualBlock main aux) = BlockProtocol main

instance LedgerSupportsProtocol main

`      `=> LedgerSupportsProtocol (DualBlock main aux) where

`  `ledgerView = ledgerView . dlMain

The block configuration we need is the block configuration of both blocks:

data instance BlockConfig (DualBlock main aux) = DualConfig {

**This document was truncated here because it was created in the Evaluation Mode.**
