# Slow and steady wins the race: network evolution for network growth
### **After a successful start to Cardano’s smart contract era, we’ll soon make the first in a program of network adjustments to support future growth**
![](img/2021-11-22-slow-and-steady-wins-the-race-network-evolution-for-network-growth.002.png) 22 November 2021![](img/2021-11-22-slow-and-steady-wins-the-race-network-evolution-for-network-growth.002.png)[ John Woods](tmp//en/blog/authors/john-woods/page-1/)![](img/2021-11-22-slow-and-steady-wins-the-race-network-evolution-for-network-growth.003.png) 8 mins read

![John Woods](img/2021-11-22-slow-and-steady-wins-the-race-network-evolution-for-network-growth.004.png)[](tmp//en/blog/authors/john-woods/page-1/)
### [**John Woods**](tmp//en/blog/authors/john-woods/page-1/)
Director of Cardano Architecture

Engineering

- ![](img/2021-11-22-slow-and-steady-wins-the-race-network-evolution-for-network-growth.005.png)[](mailto:john.woods@iohk.io "Email")
- ![](img/2021-11-22-slow-and-steady-wins-the-race-network-evolution-for-network-growth.006.png)[](https://www.linkedin.com/in/johnalanwoods/ "LinkedIn")
- ![](img/2021-11-22-slow-and-steady-wins-the-race-network-evolution-for-network-growth.007.png)[](https://github.com/johnalanwoods "GitHub")

![Slow and steady wins the race: network evolution for network growth](img/2021-11-22-slow-and-steady-wins-the-race-network-evolution-for-network-growth.008.jpeg)

From its conception, Cardano has been architected as a platform to best balance the perennial trade-offs of security, scalability and decentralization. Therefore we have architected and built a solid and secure network layer, yet with the flexibility to grow and scale to support a global base of millions of users. 

With a secure, highly decentralized proof of stake network now firmly established, and core smart contract capability deployed, we’re now heading into the Basho phase, focused on optimization, scaling and network growth. 

As a decentralized permissionless blockchain, Cardano is open to anyone who wants to use it or build on it. Recent hard forks (adding native tokens and smart contract capability) have brought many new users into the Cardano ecosystem, and we have seen rapid growth (and spikes) in transaction volumes and network traffic. 

As core components – including wallet connectors and the Plutus Application Backend (PAB) are finalized and integrated into mainnet, we anticipate significant growth in network activity. A constellation of projects [building on Cardano](https://github.com/input-output-hk/essential-cardano) will begin to launch, first on testnet then mainnet. These will only increase, with potentially hundreds of thousands of new users coming into Cardano over the coming months, from all sides of the blockchain spectrum. 

Inevitably, we can expect significant traffic around the launch of new decentralized applications (DApps), especially in the early days and weeks. To accommodate this ongoing growth, and ensure that Cardano maintains its resilience and robustness, we’re now starting to make a series of adjustments to network parameters. These parameter changes will provide ongoing improvements and enhancements to Cardano's usability and experience across its entire range of users. 
### **Architected for growth**
Ouroboros is designed to handle a large volume of data as well as transactions and scripts of different complexity and size. At present, and with current parameters, the Cardano network is utilizing on average only around 25% of its capacity. This is sub-optimal because in fact, the most efficient scenario is that Cardano runs at or close to 100% of its capacity (i.e., the network is ‘saturated’). 

While many networking solutions would suffer under such conditions, both Ouroboros and the Cardano network stack have been designed to be fair and highly resilient, even under heavy saturation. 

Efficient systems are designed to minimize congestion while enabling effective management when it does happen. You can read more in [this recent blog](https://iohk.io/en/blog/posts/2021/10/21/cardano-robust-resilient-and-flexible/), but in short, the network uses backpressure to manage the overall system load. So while some individual users during a large NFT drop may experience longer wait times for their transactions, this does not mean that the network is ‘struggling’. It actually means the network is performing as intended. We call it ‘graceful degradation’ and you can study this in greater depth in the network design paper.
### **Adjusting parameters**
Aside from the original architectural design, and significant benchmarking across a range of simulated situations, it is only in the real world that we can truly gauge demand and the effectiveness of any changes. 

Following extensive benchmarking, and developer feedback, we’re now starting to make gradual adjustments and have today submitted two initial changes.These changes are planned to take effect on the testnet on Thursday 25th November. Once tested, we anticipate subsequently applying these to the mainnet, taking effect on epoch 306, on Wednesday December 1, 2021 at 21:45:00 UTC.

So what are we adjusting?

**We’re increasing block size by 8KB to 72KB (12.5% increase)**

There are now well over 2 million Cardano wallets in use and traffic has grown by over 20 times in a year (from less than 10,000 transactions per day in November 2020 to over 200,000 transactions per day. Because of the anticipated rise in traffic as developers roll out new DApps, the block size is quickly becoming a key consideration. Larger block sizes mean that more transactions can fit into a block, thus providing greater capacity for users. Being able to fit 12.5% more transactions into a block is significant, as it means that we’re processing more transactions per second or we argue – [a more useful metric](https://www.youtube.com/watch?v=gpSnyCn2s9U) – greater data throughput.

We are taking a steady, methodical approach to changes in Cardano's parameterization. A 12.5% increase is sizable, but not too big. It leaves room for further expansion, and allows stake pool operators (SPOs) to adjust to the increased demands. We will take a 'slow and steady' approach to further block size changes so that we make the underlying network capacity available to end users, while ensuring that we can continue to operate successfully as a globally decentralized blockchain. The current generation of Ouroboros (named Praos) has specific requirements which must be satisfied in order to ensure its security goals are met, one of the most important parameters is block propagation time. Block propagation time is a measure of how long it takes for a freshly minted block to be propagated across nodes on the network representing 95% of the staked ada. For Praos to stay secure the network must propagate new blocks within 5 seconds. 

We can consider this 5s limit a ‘budget’ we can ‘spend’ on things like increasing the block size. Changes such as increased block size will naturally increase the time needed to propagate blocks, so we must monitor carefully to ensure changes we make to increase performance don’t affect the security of the network. In future iterations of Ouroboros this budget will be increased. Meanwhile our focus will be on maintaining security while flexing the network to growing demand. 

**We’re also increasing of Plutus script memory units per transaction to 11.25 million (again, 12.5% increase)**

This is a powerful change and one that we know DApp developers will very much appreciate. An increase in Plutus memory limits means that they can develop more sophisticated Plutus scripts, or that existing scripts will be able to process more data items, increase concurrency, or otherwise expand their capabilities. This will be the first of a series of changes to the memory unit settings that will greatly enhance the real-world capabilities of Plutus scripts. As with block sizes, we will roll out the changes gradually, but steadily, so that the network and SPOs adjust to the increased demand.

The changes described below (block size increase and Increase of Plutus script memory units per transaction) were requested by many app developers, for example. Both these changes go hand-in-hand. It’s not just about creating more complex scripts. It’s also about putting *more* data through.
### **Steady and sure**
As the Cardano platform evolves, every change will be carefully considered and once actioned, subsequently monitored to gauge its impact on performance. All changes will be based on empirical data drawn from the network and based on real, sustained user demand. Critically, it is important not to make decisions with a long-tail impact around short-term surges in network usage. We won't make changes prematurely or make them at a pace that could potentially compromise Cardano's longer-term security, for example. 

Cardano development is grounded in both fundamental and ongoing research. Further network enhancements in the mid-longer term will collectively deliver substantial capacity improvements, as well as tuning the network to deliver the best overall experience. 

I’ll be joining the November Cardano360 to share further thoughts on this. But in short, this is about building new and capable blockchain infrastructure, built on advanced and fundamentally decentralized technologies. Initially, we will focus on a number of performance improvements that will enable us to exploit the limits of the Ouroboros Praos protocol. We will then focus on optimizing the size of Plutus scripts and the underlying performance of the Plutus interpreter and Cardano node implementations. This will allow us to process more useful work within the same protocol parameters. Related to this will be the use of compression techniques, to reduce the size of scripts and transactions, meaning that more transactions can be carried within the same sized block. All of this (and more) will improve layer 1 performance and capacity. Looking ahead, Hydra will then introduce a layer 2 solution, providing hugely increased scalability by allowing users to provision multiple chains that reuse the same ledger representation. 
### **In conclusion**
Cardano is, in a manner of speaking, a living entity that grows and adapts with every evolutionary step. It may sound like a contradiction in terms, yet while its foundations are formed from rock-solid fundamental research, flexibility (to change even entire protocol changes via the hard fork combinator (HFC) has been designed in from the beginning. 

Parameterization changes are part of this transformative process. While inevitably there will be folks who want to move faster, our focus will remain on steady, secure evolution as Cardano grows in reach and adoption. 

*Thanks to Duncan Coutts, Kevin Hammond, and Fernando Sanchez for their contributions to this article.*
