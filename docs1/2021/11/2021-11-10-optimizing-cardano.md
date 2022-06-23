# Optimizing Cardano
### **The path to network optimization lies in gradual step-by-step adjustments**
![](img/2021-11-10-optimizing-cardano.002.png) 10 November 2021![](img/2021-11-10-optimizing-cardano.002.png)[ Tim Harrison](tmp//en/blog/authors/tim-harrison/page-1/)![](img/2021-11-10-optimizing-cardano.003.png) 10 mins read

![Tim Harrison](img/2021-11-10-optimizing-cardano.004.png)[](tmp//en/blog/authors/tim-harrison/page-1/)
### [**Tim Harrison**](tmp//en/blog/authors/tim-harrison/page-1/)
VP of Community & Ecosystem

Communications

- ![](img/2021-11-10-optimizing-cardano.005.png)[](mailto:tim.harrison@iohk.io "Email")
- ![](img/2021-11-10-optimizing-cardano.006.png)[](https://uk.linkedin.com/in/timbharrison "LinkedIn")
- ![](img/2021-11-10-optimizing-cardano.007.png)[](https://twitter.com/timbharrison "Twitter")
- ![](img/2021-11-10-optimizing-cardano.008.png)[](https://github.com/timbharrison "GitHub")

![Optimizing Cardano ](img/2021-11-10-optimizing-cardano.009.jpeg)

As a proof-of-stake blockchain, Cardano is built to be highly secure and resilient to network failures. Driven by the Ouroboros consensus algorithm, built-in Haskell that uses formal methods, and peer-reviewed academic research, Cardano is designed to provide a rock-solid environment to process millions of transactions globally, in a decentralized and highly scalable manner. 

In our [previous blog post](https://iohk.io/en/blog/posts/2021/10/21/cardano-robust-resilient-and-flexible/), we discussed network performance â€“ how the system works as a whole when processing, verifying, and signing transactions. Getting this right at the very earliest design stage is crucial if you want a system that is built for the long term. Yet, network capacity is a valuable resource, so for the most efficient performance metrics, it is essential that computation, memory, storage, and network resources are consumed effectively. 

Cardano is built to be flexible. It is designed to maximize throughput while allowing for responsiveness to increasing demand. As the network grows, we are tuning protocol parameters to adjust to pricing fluctuations, extend scalability and throughput properties. So letâ€™s take a closer look at how we will be optimizing network performance over time.
## **Defining congestion**
Efficient systems â€“ from networks to roads â€“ are built to minimize congestion, while enabling effective management when it does happen. In blockchain terms, congestion implies that the network is oversaturated and experiences difficulties when processing large volumes of transactions and signing associated blocks. On average, Cardano blocks are approximately 25% utilized across a given epoch, which shows that generally, the network is *not* congested and thereâ€™s significant spare capacity to process an even larger number of transactions. 

Cardano is designed to be fair and highly resilient even under heavy saturation. Letâ€™s remind ourselves about the current parameter settings and look at future optimizations that are planned. Current performance metrics depend on the following measures:

- **Throughput** â€” the volume of transferred data. The current block size is set to 64 KB. A single Plutus script transaction is currently limited to 16 KB, and simple transactions can commonly take up to around 300 bytes. These measures have been balanced to ensure good network utilization while minimizing transaction latencies. If increased significantly and at once, users will face increased delay in block adoption time. That is because throughput and timeliness are in tension with each other â€“ maximizing throughput implies better network performance, but this can come at the cost of increased delay when the system is heavily saturated.
- **Timeliness** â€” i.e. the block adoption time. The total â€˜budgetâ€™ for block adoption is set to 5 seconds for a block to propagate across the network (95% of the stake) with a budget of approximately 50 milliseconds available for Plutus scripts. This is designed to allow the block to include both scripts and simple transactions without monopolization. 

Recently, users recorded an increased waiting time for transaction processing which has been caused by large NFT (non-fungible token) drops. The reason for this oversaturation lies in the fact that a high quantity of NFTs was released at once which caused the following:

- a large number of simultaneous NFT transactions
- several users trying to purchase the same NFT and thus attempting to process transactions at the same time
- simultaneous refund transactions to users who were unable to purchase the NFT

This scenario created network scarcity for the NFT sale and therefore a huge demand on the service â€“ 43,000% of the supply. It is also worth noting that the â€˜congestionâ€™ period lasted for less than one hour. 

This is a growing market and NFT creators are already starting to iterate their processes to minimize the impact of such drops on the user experience. It's still early and we are all learning fast. It should be noted that the process of minting NFTs is perfectly parallelizable, meaning there is no limit to this process. Once minted, NFTs storing the programmable swap code and assets required to transact are ready to interact with the market. 

But in the short to mid-term at least, this is a matter of building more efficient traffic systems rather than widening the roads. Some developers are already producing such systems specifically for NFT drops, which should reduce costs as well as short-term network loads.

**Decentralized exchanges (DEXs)**

Many early DApps being built on Cardano are DEXs or Decentralized Exchanges. And in some applications users tend to experience contention while placing their orders. Because the DApp design prerequisites that the whole state is kept within one UTXO (rather than spread across multiple UTXOs), there occurs a dependency of a future transaction on an output from a previous transaction. This has been widely referred to as the concurrency â€˜issueâ€™. However, trundling out that automobile analogy again, it is no more of an â€˜issueâ€™ than driving on the left is an â€˜issueâ€™ in the UK or Japan. It does require a learning curve but ultimately it is just a different way of doing things. And if a developer doesnâ€™t do it, yes, they will encounter problems! Nor is it inherently more complex â€“ just requires a different approach.

Cardanoâ€™s EUTXO model is different from the account-based model. DApps built on Cardano should move away from the single-threaded state machine style and go down a level of abstraction to the EUTXO directly, constructing a solution that involves concurrent edges in the EUTXO graph. It is important to use different sets of UTXOs thereby enforcing parallelism which will improve the throughput of the system while keeping the performance of individual operations the same. Sure, this does require a shift in mindset to any developer used to Ethereumâ€™s approach. Yet, the UTXO-based model is more secure than the account-based model because keeping all the state in a single account is more vulnerable to attacks. If using parallelism techniques correctly, users will enjoy improved results in terms of throughput and scalability whereas off-chain solutions are better applicable to UTXO ledgers. For more details read the [concurrency blog post](https://iohk.io/en/blog/posts/2021/09/10/concurrency-and-all-that-cardano-smart-contracts-and-the-eutxo-model/) and [how to build a scalable Plutus DApp](https://plutus-apps.readthedocs.io/en/latest/plutus/howtos/writing-a-scalable-app.html). Weâ€™ll publish further content on this in due course to provide additional guidance on making the most of the model. 
## **The optimization roadmap**
Our focus at launch was always to provide core capability and correctness, before optimizing. This has always been our stated goal. Weâ€™re continuing to monitor performance and benchmark adjustments. As the network grows and Cardano functions at a higher capacity, we will be adjusting the parameterization to keep up with network demand. These are gradual upgrades that will be implemented step-by-step over the next few months to ensure that changes meet the network requirements and do not compromise on different properties. 

We have carried out extensive analysis and started to implement node metrics that accurately measure the data diffusion time. Data diffusion is the process of distributing transactions and blocks across nodes that verify the blockchain. It is essential to provide nodes with the needed information so that the consensus algorithm can make its decisions.

Weâ€™ll likely be implementing an average waiting time from transaction submission to transaction adoption. Along with that, we are investigating and analyzing scenarios that will boost network performance iteratively over the short and longer term, including:

- **Block size increase** â€” increased block size means more transactions in a block. The benefit is that there will be less waiting time for transactions to be adopted by a block during the periods of network saturation. However, there is a trade-off. Larger blocks take longer to propagate across the network. This also means that nodes will need more time to verify transactions. Although the block size increase is an option to increase network performance, such changes should be executed with caution. To ensure that the increase does not compromise block adoption time, we will gradually change parameters and assess the results during high saturation periods. This is not a one-step update, but rather an iterative approach that will provide us with clear results and help ensure the most efficient adjustments. 
- **Mempool size** â€” currently, the size of the mempool is set to 128 KB, which is twice the size of the current block. The mempool works as the network buffer and may cause short delay when including transactions into a block. However, mempool size increase *wonâ€™t* improve network throughput â€“ transaction queues will stay the same. The mempool allows for a fair adoption of new transactions that enter it randomly based on the producing node that is chosen by the lottery algorithm. 
- **Script compression** â€” given that the current transaction size is set to 16 KB, weâ€™re continuing to work on compression, which allows the protocol to â€˜zipâ€™ the code in a transparent manner. This means more script transactions in one block due to their decreased size â€“ developers will be able to submit more sophisticated code compressing it to 16 KB or less, and there will be more space left for other transactions. 
## **Architecting for EUTXO**
As described in our [previous concurrency blog post](https://iohk.io/en/blog/posts/2021/09/10/concurrency-and-all-that-cardano-smart-contracts-and-the-eutxo-model/), Cardanoâ€™s EUTXO model eliminates entire classes of problems when designing DeFi applications. In addition to EUTXOâ€™s native ability to process transactions in parallel, the modelâ€™s [deterministic nature](https://iohk.io/en/blog/posts/2021/09/06/no-surprises-transaction-validation-on-cardano/) ensures that developers and users can avoid wasted â€˜gasâ€™.

That said, the EUTXO model isnâ€™t the same as the account-based model. Lifting and shifting application architecture intended for account-based systems to a EUTXO-based system will result in a suboptimal application design. Applications *designed specifically* for Cardanoâ€™s EUTXO model will provide the best user experience. 

**Weâ€™ll publish a deeper technical dive on how developers can optimize order submission and processing, for example, to the EUTXO model shortly.**
## **Iteration & Improvement**
So there is plenty of work going on behind the scenes as we continue to evolve and iterate. These are still early days, and we will continuously assess network performance and adjust parameters accordingly as we go. In the short term, weâ€™ll be able to ease NFT drop congestion by more evenly spreading the stake distribution and reward distribution computation. This will in turn enable us to increase the block size, eliminate pauses and congestion at epoch boundaries, and remove computational spikes (which can cause slower block propagation). Gradual block size increase will also let us assess the best case scenarios for network performance and these results will be soon visible on the network. 

We also plan to move the ledger state to disk storage to ease the on-chain load, alongside script compression and on-chain sharing features implementation. When finalized, they will greatly complement network adjustments. 

In the mid-term, [Hydra](https://iohk.io/en/blog/posts/2021/09/17/hydra-cardano-s-solution-for-ultimate-scalability/) will bring additional capability. Longer-term, our Chief Scientist and team continue to research other methods and mechanisms around pricing frameworks and enhancing the Ouroboros protocol to increase transaction throughput. More on this in future blog posts! 
## **Two months in**
We are just two months since the start of the smart contracts era on Cardano. Whatever the weight of expectation and anticipation around the â€˜launchâ€™, this was never going to be a one-hit upgrade. Just as it was always going to take time for the ecosystem to build momentum, there was always going to be a period of bedding in and then adjusting, as demands on the network grow. Weâ€™re on a journey and understanding community feedback remains key. Talking to many of the exciting new projects #BuildingOnCardano, weâ€™re building a better understanding of their plans and objectives â€“ along with any issues they are facing â€“ so we can support and serve as needed. Weâ€™re also closely following the community debate. 

Itâ€™s early days and weâ€™re all still learning. Yet, by design, Cardano is set up to flex and grow alongside its nascent â€“ yet already vibrant â€“ ecosystem. Letâ€™s *all* keep building!

*If you are a developer and want guidance, support, or just fancy dropping by for a chat to one of our open sessions â€“ make sure you join our* growing technical community on [*Discord*](https://discord.com/channels/826816523368005654/892858202851516457).

*My thanks to John Woods, Vitor Silva, Kevin Hammond, Duncan Coutts, Romain Pellerin, Michael Peyton Jones, Jean-Frederic Etienne & Olga Hryniuk for their support and feedback in preparing this blog post.*
