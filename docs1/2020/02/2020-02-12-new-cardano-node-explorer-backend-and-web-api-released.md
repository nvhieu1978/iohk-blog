# New Cardano node, explorer backend, and web API released
### **We’ve refreshed Cardano’s architecture – with more yet to come**
![](img/2020-02-12-new-cardano-node-explorer-backend-and-web-api-released.002.png) 12 February 2020![](img/2020-02-12-new-cardano-node-explorer-backend-and-web-api-released.002.png)[ Tim Harrison](tmp//en/blog/authors/tim-harrison/page-1/)![](img/2020-02-12-new-cardano-node-explorer-backend-and-web-api-released.003.png) 4 mins read

![Tim Harrison](img/2020-02-12-new-cardano-node-explorer-backend-and-web-api-released.004.png)[](tmp//en/blog/authors/tim-harrison/page-1/)
### [**Tim Harrison**](tmp//en/blog/authors/tim-harrison/page-1/)
VP of Community & Ecosystem

Communications

- ![](img/2020-02-12-new-cardano-node-explorer-backend-and-web-api-released.005.png)[](mailto:tim.harrison@iohk.io "Email")
- ![](img/2020-02-12-new-cardano-node-explorer-backend-and-web-api-released.006.png)[](https://uk.linkedin.com/in/timbharrison "LinkedIn")
- ![](img/2020-02-12-new-cardano-node-explorer-backend-and-web-api-released.007.png)[](https://twitter.com/timbharrison "Twitter")
- ![](img/2020-02-12-new-cardano-node-explorer-backend-and-web-api-released.008.png)[](https://github.com/timbharrison "GitHub")

![New Cardano node, explorer backend, and web API released](img/2020-02-12-new-cardano-node-explorer-backend-and-web-api-released.009.jpeg)

Today marks the culmination of considerable effort by the Cardano team: the release of a new Cardano Haskell implementation. This implementation consists of two main components: the [Cardano Node](https://github.com/input-output-hk/cardano-node) and the [Cardano Explorer Backend and Web API](https://github.com/input-output-hk/cardano-explorer). Over the past 18 months, we’ve been building a new architectural foundation that will not only prepare us for the upcoming releases for Shelley – and, thereafter, Goguen – but open the door to third-party developers and enterprise adoption.

The changes will begin with the Ouroboros update to Ouroboros BFT (Byzantine Fault Tolerance), which is tentatively scheduled for February 20. For now, Cardano’s blockchain production remains on the old implementation. After the update to Ouroboros BFT, we will be able to migrate the core nodes that create blocks, while Daedalus users will be able to upgrade later, once the compatible wallet backend is available.
## **Why now?**
The original implementation of the network node – launched in September 2017 – has taken us as far as it could. We’ve known for a long time that a new architecture is needed to achieve our roadmap, ready the system for Shelley, and provide a foundation for Goguen, as well as other future releases.

This update is about radically improving Cardano’s design, and is the first to take advantage of our work on formal methods. While the old node was monolithic – with components like the wallet backend and explorer built in – the new version is modular. This makes future integrations easier and allows the node to be more readily incorporated into other systems, such as those used by exchanges. In the new architecture, the node, wallet, and explorer exist as separate components (a new wallet backend will soon be released).
## **What’s involved?**
A significant achievement of this new implementation is the separation of the consensus layer and ledger rules. This decoupling means we are able to change the ledger rules without making changes to (or risk breaking) consensus. Following from this, when we transition into Shelley to Goguen, only the ledger rules will change. This will allow us to execute deployments more efficiently and add new features more frequently. We’ll have less to validate and test, while supporting more efficient development.

Some benefits will be immediate, and others will be realized over time. The direct benefits are that IOHK engineers will be able to innovate more easily and make changes to specific components without necessarily impacting others. The new implementation, coupled with the update to Ouroboros BFT, will also lead to significant TPS (transactions per second) performance improvements. For end-users, the benefits of this update will be cumulative, as the Cardano network profits from greater developmental support and system adaptability and portability.

This new implementation is the result of a lot of hard work. Now, we start to see the benefits of our commitment to formal methods, delivering a network that can not only scale, but remain stable while doing so. The new codebase has had substantial – and ongoing – testing, and we’ve been able to make a number of fundamental improvements without inheriting the shortcomings of the old codebase.

The new Cardano node also features an IPC interface that can be used by multiple client components, including wallets, explorers, CLI tools, and custom integration APIs and tools. This isn’t only about us being able to develop better-performing systems and applications, but others being able to as well.
## **Cardano Explorer Backend and Web API**
The [Cardano Explorer Backend and Web API](https://github.com/input-output-hk/cardano-explorer) is the new explorer backend and web API for the [Cardano Node](https://github.com/input-output-hk/cardano-node). It has been completely rewritten compared to the previous [cardano-sl explorer](https://github.com/input-output-hk/cardano-sl-explorer). It has a new modular design and consists of the following components: Cardano Explorer Node, PostgreSQL database, and Cardano Explorer Web API.

- The [cardano-explorer-node](https://github.com/input-output-hk/cardano-explorer/tree/master/cardano-explorer-node) is a client of the Cardano node. It synchronizes Byron chain data into the PostgreSQL database. The PostgreSQL database schema is a stable public interface and can be used directly for queries.
- The [cardano-explorer web API](https://github.com/input-output-hk/cardano-explorer/tree/master/cardano-explorer-webapi) is a REST API server that reads data from the PostgreSQL database. It is compatible with the old cardano-sl explorer HTTP API and old web frontend.

For more information, see the [release notes](https://github.com/input-output-hk/cardano-explorer/releases) and documentation linked therein.

This release is about preparing Cardano for what’s to come, and ensuring we have the architecture and network apparatus in place to scale, remain agile, and allow for the necessary interoperability, interactivity, and ease-of-use that industry use-cases require.

For the latest Cardano updates, visit the [Cardano forum](https://forum.cardano.org/) or follow us on [Twitter](https://twitter.com/Cardano) – and stay tuned for more information on the new wallet backend.
