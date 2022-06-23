# Introducing our new peer-to-peer (P2P) testnet
### **We are working with a small group of stake pool operators on a new P2P testnet to further drive network decentralization**
![](img/2021-12-08-introducing-our-new-peer-to-peer-p2p-testnet.002.png) 8 December 2021![](img/2021-12-08-introducing-our-new-peer-to-peer-p2p-testnet.002.png)[ Olga Hryniuk](tmp//en/blog/authors/olga-hryniuk/page-1/)![](img/2021-12-08-introducing-our-new-peer-to-peer-p2p-testnet.003.png) 3 mins read

![Olga Hryniuk](img/2021-12-08-introducing-our-new-peer-to-peer-p2p-testnet.004.png)[](tmp//en/blog/authors/olga-hryniuk/page-1/)
### [**Olga Hryniuk**](tmp//en/blog/authors/olga-hryniuk/page-1/)
Technical Writer

Marketing & Communications

- ![](img/2021-12-08-introducing-our-new-peer-to-peer-p2p-testnet.005.png)[](https://www.linkedin.com/in/olga-hryniuk-1094a3160/ "LinkedIn")
- ![](img/2021-12-08-introducing-our-new-peer-to-peer-p2p-testnet.006.png)[](https://github.com/olgahryniuk "GitHub")

![Introducing our new peer-to-peer (P2P) testnet ](img/2021-12-08-introducing-our-new-peer-to-peer-p2p-testnet.007.png)

Cardano continues to build momentum with more features and capabilities being steadily added to the blockchain. As we recently reported, we are [optimizing the network](https://iohk.io/en/blog/posts/2021/11/10/optimizing-cardano/) to increase throughput so more transactions can be processed faster, and decentralized applications (DApps) and smart contracts created and used more efficiently. This week, we have kicked off an important new initiative to support our ongoing drive toward full decentralization with the launch of a new peer-to-peer (P2P) testnet.

Cardano ensures trust and security in a decentralized setting using proof-of-stake consensus through the Ouroboros algorithm. At the heart of this are about 3,000 stake pools run by operators (SPOs) who manage the distributed nodes that power the network. Clearly, in a decentralized and distributed network, there has to be reliable communication between these nodes. Central to this and vital for verifying blockchain activities is data diffusion â€“ the process of sharing information about transactions and block distribution. This also enables the Ouroboros algorithm to make its â€˜decisionsâ€™.

Until recently, Cardano nodes established connections with peers by looking up a file that described the static configuration of the network. The system also relied on nodes set up by IOG â€“ with a community-managed and configured topology â€“ that helped to establish network connectivity (read more about [the evolution of network connectivity](https://iohk.io/en/blog/posts/2021/05/11/cardano-decentralization-continues/) here). To increase decentralization and simplify node communications, we've been establishing [a P2P network](https://iohk.io/en/blog/posts/2021/04/06/boosting-network-decentralization-with-p2p/). Direct interaction between peers streamlines communication between the thousands of distributed nodes that will maintain the network without reliance on federated relays. This will be done by automated P2P networking components. Automating the process of peer selection brings us closer to a fully decentralized network and simplifies the process of running a relay or a block-producing node.

From the early days of the [Shelley incentivized testnet](https://iohk.io/en/blog/posts/2019/10/24/incentivized-testnet-what-is-it-and-how-to-get-involved/) through to the [Alonzo testnets program](https://twitter.com/InputOutputHK/status/1423704788512952331), community-supported rollouts have been central to our approach. To expand testing of the P2P changes, we are now inviting some pool operators to a semi-public testnet. Eleven operators will help us test the automated P2P components before we expand the program more widely.
## **Whatâ€™s new?**
P2P is still an experimental feature. Although it will be part of future releases, weâ€™re not yet integrating it into all our work. The pool operators will assess the environment by configuring their nodes for direct interaction with each other. P2P capabilities will be included in the [cardano-node master branch](https://github.com/input-output-hk/cardano-node/pull/3363) and in [merged pull requests to â€˜ouroboros-networkâ€™](https://github.com/input-output-hk/ouroboros-network/pulls?q=is%3Apr+is%3Amerged+label%3Apeer2peer+label%3Anetworking+) on GitHub.

The P2P mode will enable â€˜churnâ€™ to ensure dynamic promotion and demotion of peers. Updating network configuration will also be simpler for SPOs because their nodes do not have to be restarted.

The semi-public testnet will also improve the nodeâ€™s Prometheus interface. It will include the following statistics:

- outbound connections: warm (active connections that donâ€™t participate in the consensus) and hot (active connections that take part in the consensus)
- inbound connections: warm and hot
- uni-direction/duplex connections.
## **Whatâ€™s next?**
The assessment of network connections on the semi-public testnet will help us to gather valuable feedback and catch unknown issues. Once we are satisfied, we will then be ready to invite all SPOs to test P2P node communications on the public testnet. This will mark the implementation of a smart policy for peer selection. This policy will allow defining final metrics to compare with the previous, non-P2P setting. Most importantly, weâ€™ll continue testing to verify that all the components work flawlessly in isolation as well as in combination in a wide range of network conditions.

Follow our [weekly development updates](https://roadmap.cardano.org/en/status-updates/) to find out more about P2P network development and also check out the [Ouroboros network repository](https://github.com/input-output-hk/ouroboros-network) for the latest updates.
