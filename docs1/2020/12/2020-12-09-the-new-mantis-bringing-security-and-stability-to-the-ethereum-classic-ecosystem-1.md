# The new Mantis: Bringing security and stability to the Ethereum Classic ecosystem
### **We’re committed to bringing innovation and fresh life to ETC and this is just the start**
![](img/2020-12-09-the-new-mantis-bringing-security-and-stability-to-the-ethereum-classic-ecosystem-1.002.png) 9 December 2020![](img/2020-12-09-the-new-mantis-bringing-security-and-stability-to-the-ethereum-classic-ecosystem-1.002.png)[ Niamh Ahern](tmp//en/blog/authors/niamh-ahern/page-1/)![](img/2020-12-09-the-new-mantis-bringing-security-and-stability-to-the-ethereum-classic-ecosystem-1.003.png) 6 mins read

![Niamh Ahern](img/2020-12-09-the-new-mantis-bringing-security-and-stability-to-the-ethereum-classic-ecosystem-1.004.png)[](tmp//en/blog/authors/niamh-ahern/page-1/)
### [**Niamh Ahern**](tmp//en/blog/authors/niamh-ahern/page-1/)
Education Manager

Education

- ![](img/2020-12-09-the-new-mantis-bringing-security-and-stability-to-the-ethereum-classic-ecosystem-1.005.png)[](mailto:niamh.ahern@iohk.io "Email")
- ![](img/2020-12-09-the-new-mantis-bringing-security-and-stability-to-the-ethereum-classic-ecosystem-1.006.png)[](https://www.linkedin.com/in/niamh-ahern-67849949/ "LinkedIn")
- ![](img/2020-12-09-the-new-mantis-bringing-security-and-stability-to-the-ethereum-classic-ecosystem-1.007.png)[](https://twitter.com/nahern_iohk?lang=en "Twitter")
- ![](img/2020-12-09-the-new-mantis-bringing-security-and-stability-to-the-ethereum-classic-ecosystem-1.008.png)[](https://github.com/nahern "GitHub")

![The new Mantis: Bringing security and stability to the Ethereum Classic ecosystem](img/2020-12-09-the-new-mantis-bringing-security-and-stability-to-the-ethereum-classic-ecosystem-1.009.png)

IOHK has a long association with Ethereum Classic (ETC) and its community, which preserves an untampered history free from external interference and subjective altering of transactions. Serving as the next-generation digital currency platform, ETC is built as an intuitive programming platform, which allows developers of all skill sets to build the next wave of market disrupting decentralized applications (DApps). 

The goal of ETC is to securely and methodically establish a strong ecosystem underpinned by solid foundation and core immutability. However, recent 51% attacks have put the ETC ecosystem into a precarious position, denting its confidence and challenging the community’s ability to address this issue, while representing an existential threat to its future viability. 
## **Driving innovation & future growth for ETC**
New Mantis is the only client that is written natively for Ethereum Classic and it offers unrivalled levels of assurance, security, and usability. IOHK has relaunched the Mantis project to mitigate against the recent attacks, provide enhanced security, and establish a robust means of interacting with the ETC chain. A commitment to fostering innovation and sustainability lies at the heart of the project. We are aiming to provide a steady funding income with the establishment of a proto-treasury to nurture future development and growth. This Mantis re-launch represents the culmination of a project that we've been working on for some time. Over the past few months, we have resurrected our code base, and gathered a dedicated Mantis team together who have worked hard to refine and improve the code and deliver important new features.
## **What is the Mantis project?**
Mantis is a project that is built for the community, specifically designed for the developers, wallet users, and infrastructure providers to enable direct interaction with the ETC blockchain. Essentially, it is a place where future development can evolve and be tested by the community. The Mantis release includes the following components:

- Mantis client - a CLI tool that connects to other clients in a peer-to-peer manner to allow users to communicate with the ETC chain, send and receive transactions, sync the blockchain data, execute and validate smart contracts, and deploy new smart contracts on-chain.
- Mantis wallet - a node wallet with incorporated graphical user interface (GUI), which connects to both mainnet and the Sagano and Mordor testnets. 
- Mantis faucet - enables developers to receive testnet funds for use on the Sagano and Mordor testnets.
- Mantis explorer - allows tracking recent activities and transactions in regards to the ETC chain, covering the ETC mainnet, and Sagano and Mordor testnets. 

Please visit the [Mantis website](https://mantisclient.io/) where you can download the latest version of both the Mantis client and wallet.

Mantis software implements the official Ethereum Classic specification and Ethereum Classic Improvement Proposals [(ECIPs)](https://ecips.ethereumclassic.org/) introduced by ongoing efforts and discussed across teams in the ecosystem. The project has undergone a number of enhancements in terms of adding robustness and variety to the client offering, including optimizations and network upgrades that improve network security, sustainability, and performance in the long term. It has been developed from the ground up and built in 100% Scala code, a functional programming language that offers security guarantees that other languages do not. Mantis features include stable peer discovery, pruning, fast synchronization, and newly implemented checkpointing (for 51% attack resistance) and proto-treasury (for long-term sustainability). Let’s take a closer look at these features.
## **Checkpointing**
*Persistence* and *liveness* are two crucial properties that a transaction ledger should possess. It is a proven fact that both persistence and liveness suffer when the adversarial mining power in the proof of work surpasses 50%, and in the recent year, ETC has undergone several double-spending attacks prompted by the creation of large chain reorganizations. Considering that persistence and liveness were not guaranteed within the ETC network, we sought to implement protocol changes that will re-establish persistence and liveness under current network conditions, and *checkpointing* is one of the proposed solutions. 

Checkpointing ensures that the protocol is unaltered, by using the *k* parameter, or depth parameter, where every *k* block gets irreversibly "checkpointed", meaning that no one can ever drop or revert it. A trusted authority can choose the block on which to issue a checkpoint, which means that they can decide which block becomes the canonical chain that all parties should follow. This trusted authority must run continuously and is responsible for publishing the checkpoint to the network. Checkpointing ensures that the protocol is unaltered with regards to mining. The mining rewards are not affected and the checkpointing federation can only issue checkpoints on blocks that have valid proof of work and cannot mint blocks on its own. 

Checkpointing is now implemented within the Mantis project, and according to our recent [ECIP comparison for 51% attack resistance](https://static.iohk.io/docs/etc/ecip-comparison-for-51-attack-resistance.pdf), it provides far greater, and importantly formally proven, security against these types of attacks. It is important that any 51% attack mitigation is truly robust enough to give absolute certainty to ETC holders, users, and service providers that their transactions will be secure.
## **Proto-Treasury**
For the longer-term health and success of the ETC ecosystem, we position network growth, sustainability, and innovation as key elements to ensure network security. With that in mind, we are implementing a proto-treasury system within the Mantis project to establish a steady funding income. A well-developed governance strategy will enable effective, distributed funding for the long-term development of Mantis, whereas a decentralized treasury would ensure two important things for the future of the ecosystem:

- Firstly, it would provide a permanent ongoing source of funding for the ETC network. while increasing the value of the ecosystem and promoting greater developer engagement. 
- Secondly, it would provide a distributed and transparent funding mechanism, which lets the ETC community determine its future growth and enable the sustainability required for innovation and growth.

Establishing the treasury for funding purposes ensures a clear vision of the substantial system maintenance focused to obtain innovation and diversity from other projects, including proof of stake (PoS) and newer blockchains. This solution is straightforward in its optimization for speed and implementation.

The proposal foresees to distribute 80% of existing mining rewards to miners and 20% to the proto-treasury smart contract. The treasury will be controlled by the community and will enable a decentralized, collaborative decision-making process, offering an opt-in type collaboration for those who are interested.
## **What’s next?**
As much as we’re excited about the Mantis relaunch, it should be stressed that its capability won’t be limited to just the features outlined here. Mantis is an evolving project and right now we are establishing its foundational building blocks and running rigorous security audits. Further down the road, it will see more performance improvements in terms of CPU, GPU and ASICs compatibility, a new proof-of-work consensus protocol and algorithm introduction (PRISM consensus, Keccak256 algorithm) and, of course, additional enhancements for better interoperability and speed of transaction processing. You can also find out more by reading the [Mantis documentation](https://docs.mantisclient.io/) and joining the [Mantis discord](https://discord.com/invite/7vUyWrN33p) to stay up to date on all things Mantis or Ethereum Classic. Check out the Crowdcast launch event for the full Mantis showcase (and a keynote from Charles Hoskinson) and follow the Mantis team on [Twitter](https://twitter.com/Mantis_IO/) to get the latest updates! 
