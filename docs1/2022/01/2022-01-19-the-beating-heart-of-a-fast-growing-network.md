# The beating heart of a fast-growing network
### **At the core of the Cardano network lies the node. Here’s how this integral technology will play its part as we scale Cardano during 2022**
![](img/2022-01-19-the-beating-heart-of-a-fast-growing-network.002.png) 19 January 2022![](img/2022-01-19-the-beating-heart-of-a-fast-growing-network.002.png)[ John Woods](tmp//en/blog/authors/john-woods/page-1/)![](img/2022-01-19-the-beating-heart-of-a-fast-growing-network.003.png) 5 mins read

![John Woods](img/2022-01-19-the-beating-heart-of-a-fast-growing-network.004.png)[](tmp//en/blog/authors/john-woods/page-1/)
### [**John Woods**](tmp//en/blog/authors/john-woods/page-1/)
Director of Cardano Architecture

Engineering

- ![](img/2022-01-19-the-beating-heart-of-a-fast-growing-network.005.png)[](mailto:john.woods@iohk.io "Email")
- ![](img/2022-01-19-the-beating-heart-of-a-fast-growing-network.006.png)[](https://www.linkedin.com/in/johnalanwoods/ "LinkedIn")
- ![](img/2022-01-19-the-beating-heart-of-a-fast-growing-network.007.png)[](https://github.com/johnalanwoods "GitHub")

![The beating heart of a fast-growing network](img/2022-01-19-the-beating-heart-of-a-fast-growing-network.008.jpeg)

In a [recent post](https://iohk.io/en/blog/posts/2021/11/22/slow-and-steady-wins-the-race-network-evolution-for-network-growth/), we discussed our methodical approach to preparing Cardano for its expected growth over the coming weeks and months. As more and more decentralized applications make Cardano their home, and as the decentralized finance (DeFi) and ‘[RealFi](https://iohk.io/en/blog/posts/2021/11/25/welcome-to-the-age-of-realfi/)’ ecosystem expands and evolves, the blockchain needs to be able to perform accordingly.

Cardano is entering the Basho phase with a focus on [optimization, scaling, and network growth](https://iohk.io/en/blog/posts/2022/01/14/how-we-re-scaling-cardano-in-2022/). We anticipate a significant increase in transactional traffic over the months ahead, and here’s where we start the process of flexing to meet this. Improvements to the core node are part of this and we have packed node v1.33.0 full of new features and improvements to existing elements, upping Cardano’s expressiveness and the chain’s ability to do more.
## **What's in a node?**
Node v1.33.0 – released in early January and now running on circa 80% of SPO systems – has been designed with elegance and efficiency in mind. The improvements made are designed to reduce block propagation time, so we get greater headroom to make the changes we need to accommodate DApps, decentralized exchanges (DEXs), DeFi environments, and so on.

Following the implementation of the version of the node, blocks now propagate faster. This gives us extra time that we can use to implement other enhancements.

Technical improvements included in node v1.33.0 can be broadly categorized in **RAM usage optimization** and **efficiency upgrades**.

**RAM usage optimization**

The new node supports a significant drop in memory usage because of two factors: memory compaction and more efficient memory sharing (rather than multiple instances of the same object, now multiple flows within the system will use the same object.)

Specifically, there are memory improvements in Unspent Transaction Output (UTXO) handling, stake distribution, live stake distribution and pools, and hash representation. 

These improvements are:

- UTXO handling

Node v1.33.0 uses fewer words for transaction inputs.

- Stake distribution

Stake distribution snapshots represent 35% of total live data. The new node achieves a reduction by a factor of eight by sharing and changing representation.

- Live stake distribution

Live stake distribution accounts for 22% of total live data within the system.

Node v1.33.0 saves memory in two ways:

Sharing by combining multiple maps that are keyed on stake addresses (a saving of 11 words per stake address for each map combined), and sharing of stake pool IDs (5 words).

- Hash representation

Hash representation now uses 5 words instead of 6. Since hashes are ubiquitous in the system, this change, while apparently insignificant, will lead to considerable improvements in efficiency.

**Key facts about RAM memory usage optimization**

The new node enables great savings in live data due to compaction and sharing.

**Efficiency upgrades**

Apart from making memory usage far more efficient than in previous versions, node v1.33.0 includes changes to the algorithms that Cardano uses to calculate rewards and stake distribution.

The rationale for these changes is to address the uneven network performance that occurred when calculating rewards, which led to spikes in network load. The new reward calculation algorithm is now in place, so these spikes will not happen anymore.

The algorithm to calculate the rewards has changed from “column-major” over 4,000 pools, to a “row-major” over ~1m stake addresses. This allows spreading the calculation over 3 days, instead of 1 day (4,000 blocks).

We have also made changes to make the calculation of stake distribution more efficient.

**Pipelining**

Later this year, we’ll make further significant improvements to the node. A node does a lot of work processing a block, then waits for another block to come along, etc. In between, the node is not so busy. This block propagation overhead (that is, the time interval where the node is relatively idle, often called 'dead space') can be reduced through certain techniques to make good use of that otherwise 'dead' time. This is where pipelining comes in. 

This technique coalesces the validation and propagation of blocks. Now, instead of following the process of getting a header, validate it, then get its corresponding block, validate, and then send it to peer, now we get a header, validate, and send it to the peer, without validating the block. This streamlining will give the network even more headroom to make more changes.

Pipelining will significantly increase the scope/headroom we have to make further improvements to the network by reducing the block propagation overhead ('dead time').
## **Looking ahead**
The Cardano project has always been committed to building out a secure, resilient and highly decentralized network that can meet the needs of the next decade and beyond. And taking a methodical, responsible long-term approach is central to this. As the saying goes, “Measure twice, cut once.”

With the launch of many exciting new projects on Cardano, the ecosystem will see explosive growth. Inevitably, short-term capacity will not always keep pace with demand and periods of heavy congestion will occur. This is a journey that every new chain goes through. But with careful monitoring throughout, we’ll continue to work to increase Cardano’s efficiency, throughput, and capability over the weeks and months ahead. While maintaining the considered, safe approach that has served us well to date.
##### **Fernando Sanchez contributed to this article.**
