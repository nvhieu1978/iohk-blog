# From Byron to Shelley: part two, the journey to the mainnet
### **Continuing on to Shelley with the decentralization of block production**
![](img/2020-05-11-from-byron-to-shelley-part-two-the-journey-to-the-mainnet.002.png) 11 May 2020![](img/2020-05-11-from-byron-to-shelley-part-two-the-journey-to-the-mainnet.002.png)[ Kevin Hammond](tmp//en/blog/authors/kevin-hammond/page-1/)![](img/2020-05-11-from-byron-to-shelley-part-two-the-journey-to-the-mainnet.003.png) 5 mins read

![Kevin Hammond](img/2020-05-11-from-byron-to-shelley-part-two-the-journey-to-the-mainnet.004.png)[](tmp//en/blog/authors/kevin-hammond/page-1/)
### [**Kevin Hammond**](tmp//en/blog/authors/kevin-hammond/page-1/)
Software Engineer

Engineering

- ![](img/2020-05-11-from-byron-to-shelley-part-two-the-journey-to-the-mainnet.005.png)[](https://twitter.com/inputoutputhk "Twitter")

![From Byron to Shelley: part two, the journey to the mainnet](img/2020-05-11-from-byron-to-shelley-part-two-the-journey-to-the-mainnet.006.png)

Today, weâ€™re kicking off the â€˜Friends & Familyâ€™ testnet, which will allow us to establish a robust network to test and iterate, before we roll it out to the wider community. Weâ€™ve gathered a small number of around 20 â€˜pioneersâ€™ to help us with this important initial work. By the time you probably read this, theyâ€™ll be briefed and weâ€™ll have things underway.

In [my last blog](https://iohk.io/en/blog/posts/2020/04/29/from-byron-to-shelley-part-one-the-testnets/), I outlined how the Shelley experience will roll out within clearly defined phases. These first three phases will involve exploring and testing the new Shelley capabilities via a series of testnets. I thought it might be useful to offer a glimpse ahead to provide some additional context.

The rollout of the testnets will happen very much in parallel with our continued progress towards mainnet. So alongside the work on the Haskell Shelley testnet, the mainnet will be systematically upgraded to support the Shelley era protocol, that will enable staking, delegation and metadata.

Similarly, IOHKâ€™s block-producing and public-facing relay nodes on the mainnet will be upgraded so that they are ready for Shelley, and the Blockchain Explorer, Daedalus Wallet, Wallet CLI and other user-facing software will be polished so that it can be used for mainnet.

Users will soon be able to go to the official Cardano websites or other providers such as Yoroi, to download a new wallet â€“ currently in development â€“ that will work with both Byron and Shelley era blocks. The Shelley-era Daedalus wallet will contain all the logic for staking and delegation that has been tested on the Incentivized Testnet, plus new features that are specific to the full Shelley protocol. Stakepool operators, exchanges and others will also be able to download Shelley-compatible nodes and to adapt their own software to support the new Shelley client API. However, during this period, the mainnet will still be running in Byron reboot mode with federated consensus governed by the OBFT (Ouroboros Byzantine Fault Tolerance) algorithm. Think of it as a time when forward compatibility is being integrated but not yet â€˜switched onâ€™.

The move to Shelley will be accomplished using the new [hard fork combinator](https://iohk.io/en/blog/posts/2020/05/07/combinator-makes-easy-work-of-shelley-hard-fork/) that has been developed by IOHK.The hard fork combinator allows a node to transition from one blockchain protocol to another. The Cardano node software that is running on the mainnet will gradually evolve so that it is able to deal with both Byron era and Shelley era blocks, and will be modified to include the hard fork combinator. When the time comes to move the mainnet from the Byron era to the Shelley era, IOHK will trigger a hard fork.
## **â€˜Switching onâ€™ Shelley**
This will activate the hard fork combinator within the nodes, and the nodes will then change from only producing Byron era blocks to only producing Shelley era blocks. After the hard fork, no new Byron era blocks will be recorded on the blockchain, and the nodes will be able to support distributed block production, staking and delegation. They will have seamlessly switched from the OBFT to the Ouroboros Praos consensus mechanism. We will have entered the Shelley era on the mainnet.
## **Distributed stake pools and Decentralization of Block Production**
Central to Shelley is the idea of decentralization. IOHK believes that companies, systems, and platforms run by a single individual or central authority are more vulnerable and less fair. This is why it is crucial that we move block production to our supporters rather than keeping the power contained within our organizations.

The Cardano blockchain currently operates on a federated basis. Effectively, nodes â€˜controlledâ€™ by IOHK and EMURGO are responsible for block production, while Daedalus wallet users act as the nodes of the network. Shelley will mark the â€˜beginning of the endâ€™ of that era, as we move from Byronâ€™s static federated system to an active, decentralized system.

At the moment, core nodes and relays are owned and operated by IOHK. The network propagates through relays into each individual wallet. Once the system decentralizes, nodes will be run by stake pool operators and networked with individual wallets. Once control of the system is transferred over, the community will be fully running the Cardano ecosystem.
## **Federated Block Production (Byron)**
Following the hard fork, IOHKâ€™s existing core nodes will initially produce all of the Shelley blocks, as in the Byron era. However, this will change over time, under the control of the built-in d (decentralization) parameter. This parameter can be considered as a control valve that allows increasing amounts of decentralization.

In the decentralization phase, the federated system will still produce a (steadily decreasing) portion of the blocks. As this happens, stake pools will begin registering, operating, and producing blocks and will start to earn rewards in proportion to the stake that is delegated to them. As time passes, more blocks will be made by stake pools and fewer will be made by the core consensus nodes. The balance between the two will be controlled by the d parameter.
## **Distributed Block Production (Shelley and Beyond)**
We will use metrics like the amount of ada that has been staked to determine how quickly to change the d parameter and so to decentralize the network. Once the network has fully decentralized, the stake pools will completely take over block production. At that point, we will then be able to shut down the core consensus nodes and disable the d parameter. This is the first step towards the full decentralization of Cardano. We will return to that in future blog posts, when we discuss some of the exciting developments that the Shelley mainnet will enable.

The road towards Shelley has been long but creating a global financial and social operating system takes time, scientific rigor, and the support of an informed, passionate community. As always, we thank you for your support and encourage you to follow our official channels closely as the Haskell Shelley testnet and subsequent phases roll out.
