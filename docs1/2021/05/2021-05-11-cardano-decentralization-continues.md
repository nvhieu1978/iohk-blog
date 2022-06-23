# Cardano decentralization continues: insights into our P2P deployment
### **Stake pools will soon be able to test automated peer-to-peer connections**
![](img/2021-05-11-cardano-decentralization-continues.002.png) 11 May 2021![](img/2021-05-11-cardano-decentralization-continues.002.png)[ Marcin Szamotulski](tmp//en/blog/authors/marcin-szamotulski/page-1/)![](img/2021-05-11-cardano-decentralization-continues.003.png) 5 mins read

![Marcin Szamotulski](img/2021-05-11-cardano-decentralization-continues.004.png)[](tmp//en/blog/authors/marcin-szamotulski/page-1/)
### [**Marcin Szamotulski**](tmp//en/blog/authors/marcin-szamotulski/page-1/)
Software Engineering Lead

Engineering

- ![](img/2021-05-11-cardano-decentralization-continues.005.png)[](mailto:marcin.szamotulski@iohk.io "Email")
- ![](img/2021-05-11-cardano-decentralization-continues.006.png)[](https://www.linkedin.com/in/marcin-szamotulski/ "LinkedIn")
- ![](img/2021-05-11-cardano-decentralization-continues.007.png)[](https://twitter.com/me_coot "Twitter")
- ![](img/2021-05-11-cardano-decentralization-continues.008.png)[](https://github.com/coot "GitHub")

Decentralization of the Cardano network is key to ensuring its long-term sustainability, resilience, and independence from centralized governing entities. Now that block production is [fully decentralized](https://iohk.io/en/blog/posts/2021/03/31/decentralization-to-d-0-day-and-beyond/), our next focus is on developing our decentralized stake pool operator (SPO) ecosystem to build reliable and effective connections between distributed nodes.

Giving the power to validate blocks and transactions to stake pool operators requires enhancements to the network software. The activation of the peer-to-peer (P2P) governor, along with the deployment of the connection manager, enabled the release of a private P2P testnet in late April. We are now assessing this engineering testnet before deploying a semi-public P2P testnet for a group of invited SPOs to help us test and tune.

In the [P2P governor post](https://iohk.io/en/blog/posts/2021/04/06/boosting-network-decentralization-with-p2p/), we discussed the networkâ€™s architecture and the interaction between mini protocols and the components that enable direct and automated communication between nodes. Here, we assess how the connectivity model has matured to enable automated peer connectivity and reflect on the results of the private testnet launch.
## **Evolution of network connectivity**
When Cardano was launched, the Byron network connectivity model operated in a federated state. In that setting, IOHK maintained core and relay nodes that connected to about 200 other relays (Figure 1).

![federated network connectivity](img/2021-05-11-cardano-decentralization-continues.009.png)

Figure 1. Byron federated network structure 

With the launch of Shelley last year, Cardano started functioning in a hybrid setting. This allowed stake pools to construct their P2P network manually by connecting to core and relay nodes and also to the seven federated relays that helped maintain the network during this transitional phase (Figure 2).

![Hybrid network connectivity](img/2021-05-11-cardano-decentralization-continues.009.png)

Figure 2. Shelleyâ€™s initial hybrid network structure

Since March, block production has been entirely decentralized, with stake pools following manual topologies for P2P connections. This means that SPOs have been using a list of relay nodes registered across the globe to generate their configuration for connections with other peers. To provide better efficiency, it is essential to enable automated node communication without reliance on IO-run relay nodes. Thus, the networking team is now deploying the automated P2P code, which will allow pool operators to create and run a more decentralized network. 

In this way, once the P2P mainnet is deployed, Cardano will be maintained solely by community-run nodes (Figure 3).

![p2p network](img/2021-05-11-cardano-decentralization-continues.010.png)

Figure 3. Final network structure with automated node communication
## **P2P testnet and node communication**
The first stage in the P2P rollout was the launch of the private P2P testnet last month. This has been used to test the basic capabilities of the components:

- **P2P governor**: manages hot, warm, and cold sets of peers and ensures that the node meets the target number of each type of peer. 
- **Connection manager**: creates outbound connections or registers inbound connections, tracks their state, and allows full-duplex TCP connections to be reused. 
- **Server**: accepts connections and performs dynamic rate limiting. 
- **Inbound protocol governor**: responsible for running and tracking the state of the inbound connection side. This includes tracking the state of each remote peer (cold, warm, or hot) and the state of each inbound mini-protocol. 

The P2P system was deployed in a private environment and tested between eight nodes that connected to the mainnet and established communication with active SPO relay nodes; these further connected to other relays and block-producing nodes. The system enabled nodes to discover stake pool relays using the on-chain stake pool registry, which includes the DNS name or IP address of each relay.

Test results show that the nodes could arbitrarily select peers for communication, including those from the mainnet. The use of an â€˜upstreamâ€™ metric enabled the discarding of the worst-performing peers and random selection of new peers for connection. This policy has been demonstrated in large-scale simulations (10,000 nodes), providing close-to-optimal results. In the live testing, the team saw many iterations of the optimization procedure. The team also observed that a range of peer connections occurred â€“ with both nearby and far-away peers from different locations, which was inherent to all the eight nodes run in different parts of the world.

The networking and DevOps teams are now working together to improve the testnet environment, so all SPOs invited to the semi-public testnet can establish direct peer connections. This includes work on feature enhancements and testing processes to deliver the most efficient results. Thus, to introduce new targets for local root peers, the team is finalizing the tests for such related features as targets for known, established, and active peers.

*We will be soon launching the semi-public P2P testnet, with the support of a small group of SPO partners to help with initial testing, before broadening this out to the wider SPO community. As ever, early feedback and ideas from our community are central to test, iterate, and improve processes as we progress towards a fully automated and decentralized P2P architecture for the Cardano mainnet.*

*Additional contributions from Karl Knutsson, Duncan Coutts, Neil Davies, Prashanti Naik, and Olga Hryniuk.*
