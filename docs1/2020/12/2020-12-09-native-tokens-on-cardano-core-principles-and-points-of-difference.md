# Native tokens on Cardano; core principles and points of difference
### **In yesterday’s post, we looked at the purpose and value of tokens on Cardano. Here, we dig deeper into the four principles guiding our approach, and the key advantages**
![](img/2020-12-09-native-tokens-on-cardano-core-principles-and-points-of-difference.002.png) 9 December 2020![](img/2020-12-09-native-tokens-on-cardano-core-principles-and-points-of-difference.002.png)[ Polina Vinogradova](tmp//en/blog/authors/polina-vinogradova/page-1/)![](img/2020-12-09-native-tokens-on-cardano-core-principles-and-points-of-difference.003.png) 5 mins read

![Polina Vinogradova](img/2020-12-09-native-tokens-on-cardano-core-principles-and-points-of-difference.004.png)[](tmp//en/blog/authors/polina-vinogradova/page-1/)
### [**Polina Vinogradova**](tmp//en/blog/authors/polina-vinogradova/page-1/)
Research Engineer

Engineering

- ![](img/2020-12-09-native-tokens-on-cardano-core-principles-and-points-of-difference.005.png)[](mailto:polina.vinogradova@iohk.io "Email")
- ![](img/2020-12-09-native-tokens-on-cardano-core-principles-and-points-of-difference.006.png)[](https://ca.linkedin.com/in/polina-vinogradova-62105713b "LinkedIn")
- ![](img/2020-12-09-native-tokens-on-cardano-core-principles-and-points-of-difference.007.png)[](https://twitter.com/polinavinovino "Twitter")
- ![](img/2020-12-09-native-tokens-on-cardano-core-principles-and-points-of-difference.008.png)[](https://github.com/polinavino "GitHub")

![Native tokens on Cardano; core principles and points of difference](img/2020-12-09-native-tokens-on-cardano-core-principles-and-points-of-difference.009.jpeg)

Your browser does not support the audio element.

Ethereum, custom (user-defined) tokens are implemented using smart contracts to simulate the transfer of custom assets. [Our approach with Cardano](https://iohk.io/en/blog/posts/2020/12/08/native-tokens-on-cardano/) does not require smart contracts, because the ledger itself supports the accounting of non-ada native assets. 

Another difference is that Cardano’s multi-asset ledger supports both fungible and unique, non-fungible tokens without specialized contracts (similar to those required by ERC-20 and ERC-721 tokens). It can store a mix of both fungible and non-fungible tokens in a single output. 

Cardano’s native tokens framework is based on four principles:

- lightweight
- affordability
- security
- unified process

**Lightweight**

The native token framework is based on a multi-asset ledger structure built around token bundles (values), A token bundle can contain a heterogeneous mix of ada and other tokens. These token-containing structures are stored in outputs on the ledger instead of ada, as previously. Each type of token is identified by its asset ID, which includes a hash reference to its minting policy. The minting policy itself is only ever checked during minting or burning, and is not itself stored on the ledger, which makes this approach quite lightweight.

The fungibility relationship is also captured by the asset ID in a lightweight way: tokens with the same asset ID are fungible with each other, but not fungible with those with a different asset ID. Unique tokens have a quantity of exactly 1 associated with their asset ID. 

The asset ID identifies each type of token within a single token bundle and across the whole ledger. It also identifies the token’s place in the internal two-level map structure of the token bundle. This internal data structure enables fungible and non-fungible tokens to be represented uniformly. It also gives great flexibility to the kinds of asset use cases that can be tokenized in the system. It is straightforward to represent, for example, timeshares of a single piece of property, or a selection of unique pieces of art scoped under a single minting policy controlled by the artist. 

The inherent simplicity of native tokens is further highlighted when we look at how transferring assets between two contracts works in Ethereum’s ERC-20. In this situation, smart contract code is required, which adds complexity, and with it room for error and cost. The structure of token bundles offers a rather lightweight approach to asset transfer, because different types of token can be transacted in a single transaction, with greater speed.

**Affordability**

In an ERC-20 token environment, transferring any number of tokens between two peers requires the execution of a smart contract, which carries an execution fee (gas). By contrast, in Cardano’s native multi-asset ecosystem, the transfer of assets (tokens, ada, custom currencies, etc) does not require a smart contract, and does not carry any execution fee, which means greater affordability.

**Security**

Native tokens feature a more lightweight and less costly design than that of Ethereum’s ERC-20 and ERC-721 standards. But these two features would mean nothing without a robust security layer to guarantee the integrity of the system.

In native tokens, system integrity is built around the ledger property of value preservation (that is, that the sum of all the inputs is equal to the sum of the outputs). All native token transfer logic is coded in the ledger, as opposed to user-defined smart contracts. This ensures predictable and uniform behaviour of the system, and does not require users to understand smart contracts, which can often be a point of vulnerability. 

While accounting correctness is ensured by the ledger, minting and burning of tokens is regulated by their user-defined minting policies. A minting policy is permanently hash-associated to the tokens scoped under it, and there is no way to change this policy. This guarantees that the policy an issuer chose can never be changed to allow minting or burning of this type of token which was not authorized under the original policy. Whenever a minting transaction is added to the ledger, the policy for each type of token being minted is checked and must be satisfied. Each token in circulation, except ada (as Cardano forbids minting additional ada), necessarily has a minting policy and is guaranteed to have been minted according to that policy. 

Therefore the only custom code required to manipulate tokens in Cardano is the policy itself. Tying the policy hash to the asset identifier means that there is no need for a global asset registry, so creating assets is cheap and easy. The system remains simple, lightweight and easy to use.

**Unified process**

When native tokens are implemented as part of Goguen, the ledger will handle all tokens in the same way. And minting a token can only be done in one way, to reduce ambiguity and possible mistakes or bugs. This simplification in using a unified process will lead to faster development and a better development experience overall. 
### **Pre-production environment incoming**
Native token capability will be deployed to the Cardano mainnet following a protocol upgrade in Q1 2021 (known internally by the working name, ‘Mary’) opening up a new world of use cases and opportunity. To onboard new developers ahead of this date, we’re now finalizing the deployment of a pre-production environment for native tokens. So stay close to our social channels for the very latest news on deployment.

*If you are a developer and want to get involved early on, [visit our developer site](https://developers.cardano.org/en/development-environments/native-tokens/native-tokens/), where you can get supporting documentation and resources. We’ll add to this over time; sign up to our developer survey on [this page](https://bit.ly/3lX1ER0) to express your interest and be alerted as soon as everything becomes available.*
