# Everything you always wanted to know about impermanent loss and were afraid to ask
### **How the EUTxO model is better for the predictability of impermanent loss than Accounts-based chains**
![](img/2022-05-27-everything-you-always-wanted-to-know-about-impermanent-loss-and-were-afraid-to-ask.002.png) 27 May 2022![](img/2022-05-27-everything-you-always-wanted-to-know-about-impermanent-loss-and-were-afraid-to-ask.002.png)[ Fernando Sanchez](tmp//en/blog/authors/fernando-sanchez/page-1/)![](img/2022-05-27-everything-you-always-wanted-to-know-about-impermanent-loss-and-were-afraid-to-ask.003.png) 9 mins read

![Fernando Sanchez](img/2022-05-27-everything-you-always-wanted-to-know-about-impermanent-loss-and-were-afraid-to-ask.004.png)[](tmp//en/blog/authors/fernando-sanchez/page-1/)
### [**Fernando Sanchez**](tmp//en/blog/authors/fernando-sanchez/page-1/)
Technical Writer

Marketing and Communications

- ![](img/2022-05-27-everything-you-always-wanted-to-know-about-impermanent-loss-and-were-afraid-to-ask.005.png)[](mailto:fernando.sanchez@iohk.io "Email")
- ![](img/2022-05-27-everything-you-always-wanted-to-know-about-impermanent-loss-and-were-afraid-to-ask.006.png)[](https://www.linkedin.com/in/linkedinsanchezf/ "LinkedIn")

![Everything you always wanted to know about impermanent loss and were afraid to ask](img/2022-05-27-everything-you-always-wanted-to-know-about-impermanent-loss-and-were-afraid-to-ask.007.jpeg)

**Disclaimer**: *Nothing in this article is intended to be professional advice, including without limitation, financial, investment, legal or tax advice. Input Output Global is not responsible for your use of or reliance on any information in this article.*

Decentralized Finance (DeFi) is an umbrella term that refers to decentralized applications (DApps), services, protocols, and financial instruments built on blockchain. It is a relatively new industry segment enabled by decentralized ledger technology, which means there is no single authority with centralized control over the system. And anyone familiar with the DeFi environment probably knows about impermanent loss. It's a simple concept with a misleading name.

Cardano is a third-generation blockchain whose [expansive DeFi universe](https://iohk.io/en/blog/posts/2022/01/10/defi-demystified/) features, among many other DApps, decentralized exchanges (DEXs). These are crypto exchange protocols that enable peers to trade cryptocurrencies with each other. DEXs use two main design architectures: *automated market maker (AMM)* and *order book*. The implementation of AMMs is relatively simple, and this design has since become the de facto choice for Account-based chains. However, this design has some inherent deficiencies. Their tendency to incur impermanent loss, for example.

Cardano uses an [extended unspent transaction output (EUTxO)](https://iohk.io/en/blog/posts/2021/03/11/cardanos-extended-utxo-accounting-model/) accounting model to track the movement of assets across the chain. EUTxO is deterministic, which offers better predictability of impermanent loss.

These seemingly unrelated concepts coalesce into a very interesting interplay on the blockchain. This article considers DEX designs and explains why EUTxO offers better predictability of impermanent loss than Account-based accounting models.
## **Impermanent loss: definition**
When the total value of assets provided as liquidity is lower than the value that would have accrued had you simply held onto them.

This is the simplest definition of impermanent loss, a concept that inspires dread on liquidity providers. 

Impermanent loss occurs when the price of the assets deposited into a liquidity pool changes (upwards or downwards) in relation to when they were deposited. In other words, the worth of your assets when you withdraw them is different to when you deposited them into the liquidity pool. 

The name *impermanent* is slightly misleading, as a decrease in token price might only be temporary, and the price might rise again following market or trading conditions, etc. In this case, the loss would be *temporary* (i.e., impermanent), because the price rectified upwards. The change becomes *permanent* only if the dollar price of the token at withdrawal is less than it was when the token was deposited.

You could argue that impermanent loss is the risk that liquidity providers take in exchange for fees earned by trading crypto pairs on liquidity pools. If the loss is greater than the fees earned, the liquidity provider realizes a loss, which might not have happened had they held onto their tokens instead. It is interesting to note that you might not actually lose money, but your gains might be less than if you had just held the tokens.
## **AMMs vs order-book**
Understanding impermanent loss requires a basic understanding of how DEXs work. Currently, DEXs use two design models: AMM and order book. Each comes with a set of advantages and disadvantages when it comes to impermanent loss, which are explored. below.

**AMM**

The Automated Market Maker (AMM) DEX mode enables automated trading of cryptocurrency pairs using smart contracts. These pairs are usually (but not always) an Ethereum-based token and a stablecoin.

AMMs rely on liquidity pools, which are mechanisms that facilitate users to pool their assets into smart contracts. The more liquidity there is in the pool, the easier it becomes to trade on the DEX the pool is associated with, and the higher the fees and rewards earned by liquidity providers. Liquidity pools aggregate the liquidity provided by investors into both sides of the trading pair. The pool uses an algorithm that looks at the current liquidity to calculate the pair's market price at that time. To put it another way, the algorithm considers the availability of a particular asset in the pool to determine its price.

AMMs rely almost entirely on liquidity providers to provide liquidity to expand the pool's size and ensure the assets are traded at a fair price. This design trait effectively means that the liquidity providers are the market makers.

Liquidity providers need an incentive to invest, of course. This comes in the form of yield farming, essentially token rewards earned through lending or staking of digital assets.

**Order book**

The mechanics behind the order book design have been around the economics field for a long time. It is a very straightforward model. The order book simply lists all the buy/sell (asks/bids, in this context) orders, so when the traders put in their orders, the order book sorts them according to the asset's price. If there is supply and demand, the asset can be traded.

UTXO-based ledgers, like Cardano, are far more suitable for order book architecture, as this design, together with Cardano's EUTxO features, mitigates the effects of impermanent loss. 
## **The (un)predictability of impermanent loss**
Liquidity providers provide liquidity to pools for financial returns. But this brings with it risk. The amount of tokens in the pool and number of liquidity providers contributing to it are major factors on the possibility of impermanent loss occurring, and such consideration is important for potential liquidity providers. Frequent impermanent loss leads to pools drying up and liquidity providers looking elsewhere.

Here's the insidious thing about impermanent loss: it is very difficult to predict whether or not it will occur, and to what degree.
## **Impermanent loss in UTXO-based chains vs Account-based ones**
Quick intro:

- UTXO-based chains: there are no accounts holding a balance. Instead, users' wallets keep track of a list of unspent outputs associated with all addresses owned by the user, and calculate the usersâ€™ balance. UTXO is, in many ways, similar to cash transactions. Cardano â€˜s EUTxO model adds a datum, which is contract-specific data. This is important as it confers Cardano with the ability to support multi-assets and smart contracts.
- Account-based model - This accounting model uses an account (which can be controlled by a private key or a smart contract) to hold a coin balance. In this model, assets are represented as balances within usersâ€™ accounts, and the balances are stored as a global state of accounts. The state is kept by each node and updated with every transaction.

There are several fundamental differences between these two models, but when it comes to AMMs and impermanent loss, there is one key distinction. AMMs operating on Account-based chains tend to use a Constant Formula Market Maker (CFMM) pricing formula, which is one of the more commonly used algorithms for AMMs. This formula contains inherent inefficiencies. For example, the Total Value Locked (TVL) -defined as the sum of all staked crypto assets earning rewards, interest, etc.- is distributed across the entire price range, which implies that the price of an asset is equally likely to be $1 or $10,000. Under this assumption, CFMM prices are unrealistic and tend not to reflect actual market conditions. Also, trades on low token volume tend to lead to high slippage (the difference between the expected price of an order and the price when the order actually executes.) While CFMM is a popular choice for AMMs, these inefficiencies might result in the dilution of revenues for liquidity providers. More importantly, this liquidity is subject to impermanent loss.
## **EUTxO and order book DEX design as the bulwark against impermanent loss**
EUTxO architecture's inherent advantages of security, [determinism](https://www.essentialcardano.io/glossary/determinism), [parallelism](https://www.essentialcardano.io/article/concurrency-and-all-that-cardano-smart-contracts-and-the-eutxo-model), and scalability offer an ideal environment for DEXs using order book design, as it presents stronger resilience to impermanent loss. One key advantage of this design is concentrated liquidity (liquidity that is allocated within a custom price range.) This feature maximizes the liquidity's efficiency and minimizes impermanent loss.
## **Why global state is not an issue in EUTxO-based chains**
Unlike Account-based blockchains where every single transaction outcome alters the global state, in UTXO-based blockchains, the validity of a transaction is assessed at the transaction level, and the balance is the sum of remaining UTXOs. At the local state, in other words. 

This immediately poses a problem for Account-based chains. A multitude of smart contracts and other actors continuously interact and influence the global state, which means that assets and resources are consumed, and gas prices rise and fall all the time. A side effect of this is that transaction fees can (and do) fluctuate. Effectively, this means that a transaction's gas fees might spike significantly in the interval between the transaction being submitted and validated. Consequently, such a transaction might not be accepted by the chain, but the gas fees are taken anyway, potentially leading to financial loss for the user. This is one of the Ethereum chain's main design flaws.

Fee wastage cannot occur in Cardano's EUTxO model, since transactions are processed and validated at the local state. This is achieved by adding a datum (additional data) to the transaction. The datum contains contract-specific information, which is passed to the transaction's validation logic, thus maintaining EUTxO's deterministic context. This effectively means that transaction fees are known in advance, and will not change. A welcome side effect of EUTxO and determinism is that transactions cannot be rearranged by bad actors, another risk of Account-based models.

The local nature of transaction validation offers yet another significant advantage: a high degree of parallelism. A node could validate transactions in parallel, as long as those transactions do not attempt to consume the same input. This cannot be done in Account-based chains, as transactions must be processed sequentially by design.
### **Further enhancements**
The Plutus platform provides a native smart contract language for the Cardano blockchain. Upcoming Cardano Improvement Proposals (CIPs) to Plutus include:

[CIP-31](https://cips.cardano.org/cips/cip31/): Reference Inputs [CIP-32](https://cips.cardano.org/cips/cip32/): Inline Datums [CIP-33](https://cips.cardano.org/cips/cip33/): Reference Scripts CIP-40: Collateral Outputs

**Key takeaways**:

- Impermanent loss is the net difference between the value of two cryptocurrency assets in a liquidity pool-based AMM.
- The impermanent loss is calculated by comparing the value of the tokens at withdrawal against the value of just holding them.
- Stablecoins have price stability, so liquidity pools that utilize stablecoins can be less exposed to impermanent loss.
- UTXO-based chains using order book DEX design are more resilient to impermanent loss than AMM DEXs on Account-based chains.
- Fee wastage cannot occur in the EUTxO model, since transactions are processed and validated at the local state.
