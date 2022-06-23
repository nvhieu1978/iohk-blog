# Architecting DApps on the EUTXO ledger
### **Taking a closer look at ways of DApp architecture on Cardano**
![](img/2021-11-16-architecting-dapps-on-the-eutxo-ledger.002.png) 16 November 2021![](img/2021-11-16-architecting-dapps-on-the-eutxo-ledger.002.png)[ Jean-Frédéric Etienne](tmp//en/blog/authors/Jean-Frédéric-Etienne/page-1/)![](img/2021-11-16-architecting-dapps-on-the-eutxo-ledger.003.png) 5 mins read

![Jean-Frédéric Etienne](img/2021-11-16-architecting-dapps-on-the-eutxo-ledger.004.png)[](tmp//en/blog/authors/Jean-Frédéric-Etienne/page-1/)
### [**Jean-Frédéric Etienne**](tmp//en/blog/authors/Jean-Frédéric-Etienne/page-1/)
Software Engineer

Engineering

- ![](img/2021-11-16-architecting-dapps-on-the-eutxo-ledger.005.png)[](mailto:jean-frederic.etienne@iohk.io "Email")
- ![](img/2021-11-16-architecting-dapps-on-the-eutxo-ledger.006.png)[](https://www.linkedin.com/in/jean-frédéric-etienne-89607a130 "LinkedIn")
- ![](img/2021-11-16-architecting-dapps-on-the-eutxo-ledger.007.png)[](https://twitter.com/JeanFrdricEtie1 "Twitter")
- ![](img/2021-11-16-architecting-dapps-on-the-eutxo-ledger.008.png)[](https://github.com/etiennejf "GitHub")

![Architecting DApps on the EUTXO ledger](img/2021-11-16-architecting-dapps-on-the-eutxo-ledger.009.jpeg)

Following up on our recent blog post about [Cardano’s performance and ledger optimization roadmap](https://iohk.io/en/blog/posts/2021/11/10/optimizing-cardano/), we prepared a deeper technical dive into the architecture of the EUTXO ledger. 

Here, we offer an example architecture and also discuss possible improvements that will boost transaction throughput and minimize delays in transaction processing. 

Cardano’s EUTXO model is a solid basis for decentralized finance (DeFi) and decentralized applications (DApp) development as it facilitates parallel transaction processing, which enables greater scalability than compared to account-based models, as well as providing enhanced security settings. 

However, using a design or mechanisms applicable to account-based systems rather than the EUTXO model (in particular, when building decentralized exchanges) may result in contention issues. This results in a situation when a new transaction is dependent on the output of a previous transaction thus causing delays, especially if there is a large number of transactions. To eliminate this issue, developers should avoid using a single-threaded state machine style and design applications specifically taking into account EUTXO properties. 
## **What does a well-formed architecture look like?**
An [order book pattern](https://www.google.com/url?q=https://plutus-apps.readthedocs.io/en/latest/plutus/explanations/order-book-pattern.html%23what-is-the-order-book-pattern&sa=D&source=docs&ust=1636717791363000&usg=AOvVaw1XLRJgIX-WV7BDp-_EO-A_) is one of the approaches applicable to DEX development if compatible with smart contract logic. And most of the protocol architectures evaluated and presented in [SundaeSwap’s blog post](https://sundaeswap-finance.medium.com/sundaeswap-labs-presents-the-scooper-model-678d6054318d), rely on a general approach whereby:

- a user locks funds in an intermediate script (which we will call the ***request*** script) together with a description of the submitted orders (e.g., token or datum)
- a third party (referred to as a *batcher*) aggregates the orders sitting at the ***request*** script into one single transaction such that:
  - the locked orders are spent together with the UTXO holding the global state of the ***main*** script (e.g., liquidity pool) to be updated
  - results of executed orders are sent back to the original users
  - a new UTXO holding the updated global state resides at the ***main*** script address

When adopting such a batching pattern, one should bear in mind that, whenever *N* orders sitting at the ***request*** script are consumed within a single transaction, the ***request*** script will be executed *N* times on transaction submission. Moreover, the memory limit check (triggered when the transaction is submitted) is realized by aggregating the memory consumption for each single ***request*** script execution, for the *main* script execution, and for any MintingPolicy scripts that may also be executed (i.e., according to protocol design). Additionally, the same transaction context, which is proportional to the number of orders spent, will be passed as an argument for each script execution. 

Although this is a good approach, there are possible improvements to make it even better.

One potential solution to avoid triggering the execution of the ***request*** script *N* times (i.e., within the aggregated transaction) is for the user to directly submit orders to their own public key address instead. The ***request*** script is solely used to notify the presence of pending orders and to lock transaction fees that can afterward be claimed by the *batcher* once orders have been processed. Using this solution, users are also required to sign the aggregated transaction to authorize the spending of orders. It is also important to note, that in such a case, all users in the batch should be online to participate. A simplified architecture for such a solution can be summarized as follows:

**Order submission**:

- A specific MintingPolicy script can be used to mint an ‘order’ token submitted to the user's public key address.
- The hash of the user's public key address, together with the order description and any necessary transaction fees, can be sent to the request script for order notification.

**Order processing**:

- The *batcher* inspects the UTXOs sitting at the request script address to collect ‘order’ tokens and build the aggregated transaction, such that the ‘order’ tokens are used by the main script to validate the aggregated transaction. Note that if an ‘order’ token is not present at the corresponding public key address, the order is considered void.
- The UTXOs sitting at the request script are not spent by the aggregated transaction. They are only used to collect the UTXOs holding the ‘order’ tokens.
- The *batcher* notifies the relevant users to sign the aggregated transaction for submission.
- A MintingPolicy, bound to the main script, is used to mint a ‘receipt’ token for each processed order. This ‘receipt’ token will be used by the *batcher* to claim the transaction fees locked at the request script.

**Transaction fee collection:**

- The *batcher* can consume each UTXO sitting at the request script by providing the corresponding ‘receipt’ token. 

Benchmarks conducted on the public testnet show that with this simple architecture, around 25 to 30 orders can easily be handled within one single transaction, without exceeding the memory limits of 10 million units. We believe that some additional optimizations can still be performed to increase this figure.

Developers can also extend this architecture to consider more sophisticated mechanisms guaranteeing deterministic ordering, order cancellation by users within a specific time frame, and additional protection against malicious batchers. 

This is just one example of how one can take a EUTXO specific approach to DApp design. We are in the process of extending our documentation and will share other examples in due course. Currently, you can find some code samples for [avoiding concurrency using multi signatures here](https://github.com/input-output-hk/lobster-challenge/tree/concurrency-multisig). 

We also anticipate that the development community will identify many further models and we’ll be happy to include these in our repos to build a body of resources for the Plutus development community over the months ahead.

*Thanks to John Woods and the team for their input and support in preparing this blog post.*
