# From node enhancement to block leadership… Cardano’s February release
### **In 2022 we’re grouping multiple code releases to improve delivery predictability for the ecosystem. Here’s what’s coming in our first major update of 2022**
![](img/2022-02-28-from-node-enhancement-to-block-leadership-cardano-s-february-release.002.png) 28 February 2022![](img/2022-02-28-from-node-enhancement-to-block-leadership-cardano-s-february-release.002.png)[ Tim Harrison](tmp//en/blog/authors/tim-harrison/page-1/)![](img/2022-02-28-from-node-enhancement-to-block-leadership-cardano-s-february-release.003.png) 4 mins read

![Tim Harrison](img/2022-02-28-from-node-enhancement-to-block-leadership-cardano-s-february-release.004.png)[](tmp//en/blog/authors/tim-harrison/page-1/)
### [**Tim Harrison**](tmp//en/blog/authors/tim-harrison/page-1/)
VP of Community & Ecosystem

Communications

- ![](img/2022-02-28-from-node-enhancement-to-block-leadership-cardano-s-february-release.005.png)[](mailto:tim.harrison@iohk.io "Email")
- ![](img/2022-02-28-from-node-enhancement-to-block-leadership-cardano-s-february-release.006.png)[](https://uk.linkedin.com/in/timbharrison "LinkedIn")
- ![](img/2022-02-28-from-node-enhancement-to-block-leadership-cardano-s-february-release.007.png)[](https://twitter.com/timbharrison "Twitter")
- ![](img/2022-02-28-from-node-enhancement-to-block-leadership-cardano-s-february-release.008.png)[](https://github.com/timbharrison "GitHub")

![From node enhancement to block leadership… Cardano’s February release](img/2022-02-28-from-node-enhancement-to-block-leadership-cardano-s-february-release.009.jpeg)

Following the deployment of smart contract capabilities with the Alonzo update, Cardano is now focused on performance optimization and scalability. We’re now starting to see a diverse range of decentralized applications (DApps) and exchanges (DEXs) launch, with many more to come over the months ahead. 2022 is the year when Cardano starts evolving into a platform to provide sustainable finance ([RealFi](https://iohk.io/en/blog/posts/2021/11/25/welcome-to-the-age-of-realfi/)) for real people, and an environment where future developments will be regulated by a framework of decentralized governance. 

Throughout the coming weeks and months, we will be optimizing, scaling and bringing new features through new release deployments. We will do this in well-defined incremental updates that groups new features for our technology stack into more manageable periodic releases. We’re now in the very final stages of preparing our February release, the first of three major code drops (June and October will follow) upgrading the core network in 2022.

This grouping strategy has one clear rationale: predictability. Cardano has grown significantly, and it's expected to grow even more as 2022 goes on. By creating specific release windows, companies that rely on Cardano's infrastructure know exactly when major releases are coming, so they can prepare accordingly.
### **Coming in this release**
The first major release of 2022 contains some powerful improvements and enhancements:

- Ability to create transactions conforming to the Concise Data Definition Language (CDDL) using native tools CLI that ship with the node, rather than requiring third-party tools.
- Multi-signature of transactions in incremental stages. While it is already possible to have a Cardano transaction signed by multiple entities (something similar to a joint bank account) using their private keys, this update makes it possible to sign a transaction incrementally. Now, for example, one party can sign the transaction first, then send it over to someone else, instead of having to sign it together.
- New CLI tool for SPOs to check the leadership schedule. This tool enables SPOs to review the next epoch and check the slots where the SPO that is executing the command will mint a block. Some might think that this ability might raise security questions, but the tool is designed in such a way that any given SPO can only check their own upcoming schedule. They cannot check any other SPO's schedules.
- CLI tool for local mempool inspection. This is a developer tool that enables inspection of the local mempool where transactions sit before they are included in a block. This feature allows developers to follow a transaction's progress before it gets added to a block. 
- CLI tool to estimate script cost. Node users will now be able to accurately estimate the cost of running a Plutus script. The utility of this is that it enables developers to look at the resources (memory limits, CPU limits, etc.) they use when writing smart contracts or validation scripts, which is very useful when crafting Plutus transactions. Now, developers can know how much resources will their scripts use when executing on-chain.

Our February release is just the start. [Throughout 2022](https://iohk.io/en/blog/posts/2022/01/14/how-we-re-scaling-cardano-in-2022/) – and focused around June and October hard fork combinator (HFC) events – we will introduce an array of scaling enhancements. These include key elements of our scaling plan like pipelining, new Plutus CIPs, UTXO on-disk storage and Hydra. In combination with parameter adjustments, these features will enhance Cardano's throughput and optimize the system to accommodate an increasing range of decentralized finance (DeFi) apps, smart contracts, and DEXs. Plus as outlined in our recent Cardano360 February show, IOG is working across a host of new products and features, from a DApp store and a new light wallet product, to Mithril fast sync solution and sidechains. All the while an incredible community contributes new DApps, services, sites, tools and APIs to keep building out a flourishing decentralized ecosystem. An exciting 2022 lies ahead. Onwards…
