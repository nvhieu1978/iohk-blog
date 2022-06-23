# Ouroboros Chronos provides the first high-resilience, cryptographic time source based on blockchain technology
### **Designed to provide more accurate global timekeeping, Chronos ensures increased security and network resilience to communication delays**
![](img/2021-10-27-ouroboros-chronos-provides-the-first-high-resilience-cryptographic-time-source-based-on-blockchain.002.png) 27 October 2021![](img/2021-10-27-ouroboros-chronos-provides-the-first-high-resilience-cryptographic-time-source-based-on-blockchain.002.png)[ Olga Hryniuk](tmp//en/blog/authors/olga-hryniuk/page-1/)![](img/2021-10-27-ouroboros-chronos-provides-the-first-high-resilience-cryptographic-time-source-based-on-blockchain.003.png) 5 mins read

![Olga Hryniuk](img/2021-10-27-ouroboros-chronos-provides-the-first-high-resilience-cryptographic-time-source-based-on-blockchain.004.png)[](tmp//en/blog/authors/olga-hryniuk/page-1/)
### [**Olga Hryniuk**](tmp//en/blog/authors/olga-hryniuk/page-1/)
Technical Writer

Marketing & Communications

- ![](img/2021-10-27-ouroboros-chronos-provides-the-first-high-resilience-cryptographic-time-source-based-on-blockchain.005.png)[](https://www.linkedin.com/in/olga-hryniuk-1094a3160/ "LinkedIn")
- ![](img/2021-10-27-ouroboros-chronos-provides-the-first-high-resilience-cryptographic-time-source-based-on-blockchain.006.png)[](https://github.com/olgahryniuk "GitHub")

![Ouroboros Chronos provides the first high-resilience, cryptographic time source based on blockchain technology](img/2021-10-27-ouroboros-chronos-provides-the-first-high-resilience-cryptographic-time-source-based-on-blockchain.007.jpeg)

Global time synchronization across any distributed network is essential to ensure its resilience.

From ensuring up-to-date information between all participants, maintaining accurate transaction processing and block creation, time synchronization is especially important in terms of smart contract deployment. 

In collaboration with scientists from the Universities of Edinburgh, Purdue, and Connecticut, Input Output found a way to globally synchronize clocks across a blockchain to provide a more secure and tamper-proof global time source. This includes synchronization of time from internet of things (IoT) devices, like measurement tools in supply chains, and general distributed systems, particularly where the disruption of a central clock represents a security risk. The research is realized by Ouroboros Chronos, the Greek word for time, which is the latest iteration of Ouroboros â€“ the consensus algorithm that underpins the Cardano blockchain.
## **Time matters**
Time is an indispensable concept within computer programs and applications. Without this concept, we would not be able to access any transport layer security (TLS) based websites, exchange data, or utilize various cryptographic algorithms. 

Yet, time tracking is a difficult problem to solve. Accurate time synchronization presumes data transmission across the whole internet, and this, in turn, takes time too. It is also hard to predict how much time would be required for certain data transmission â€“ the network state constantly changes and relies on such factors as congestion and the actual size of data among others. Thus, inconsistencies often occur and it is important to provide the tools and solutions for accurate timekeeping.
## **Real time**
With common computers, we take timekeeping for granted. However, there is a rigorous mechanism that works behind the scenes. The [Network Time Protocol](http://ntp.org/) (NTP), for instance, addresses the timekeeping issue using a hierarchy of servers distributed globally. This includes up to 15 Stratums the routing paths of which are developed to synchronize in the most optimized manner. This is also enabled by the construction of a [Bellman-Ford](https://en.wikipedia.org/wiki/Bellman%E2%80%93Ford_algorithm) shortest-path spanning tree that decreases both latency and transmission time inconsistencies.

The UK Governmentâ€™s [Satellite-derived time and position: Blackett review](https://www.gov.uk/government/publications/satellite-derived-time-and-position-blackett-review) recently highlighted the need for more resilient timing data and the dangerous dependence of critical sectors from smart grids to autonomous vehicles on Global Navigation Satellite Systems (GNSS) that are vulnerable to jamming, cyber attacks, and space weather. Additionally, the worldâ€™s first [National Timing Centre](https://www.gov.uk/government/news/worlds-first-timing-centre-to-protect-uk-from-risk-of-satellite-failure), led by the National Physical Laboratory, was recently created to investigate alternative and more resilient timing services for everything from telecommunications to smart transport. International metrology centers currently have to [compare clocks](https://www.npl.co.uk/time-frequency/comparison-dissemination) operating at different frequencies and in multiple locations for accuracy.
## **Blockchain time synchronization**
The concept of timekeeping is different for distributed ledger technology. Without an accurate and valid timestamp, the network cannot verify if the transaction that is being processed is valid and does not revert the previous one. There are different timestamping techniques used across a range of blockchain ledgers, however, they arenâ€™t necessarily very accurate. For example, Bitcoin uses timestamps for consensus security reasons, but not primarily for timekeeping; and in Ethereum, on-chain timestamps are determined by miners whereas the consensus wonâ€™t technically block or verify those for validity.

Timekeeping is essential for smart contract execution as well. Inaccuracy poses a risk for decentralized finance (DeFi) smart contract attacks. Smart contract vulnerabilities arenâ€™t always conditioned by poor code, time inconsistencies should be resolved to block any possible attacks within the ledger.
## **Ouroboros Chronos: designed to boost communication and timing resilience**
The new research on Ouroboros Chronos enables blockchain technology to synchronize clocks more securely. Chronos is itself a cryptographically secure blockchain protocol that additionally provides an accurate source of time via a novel time synchronization mechanism, eliminating the vulnerabilities of externally hosted clocks. This also enables blockchain to accurately time-stamp transactions making the ledger more resistant to attacks that target time information.

The new protocol can dramatically boost the resilience of critical telecommunications, transport, trading systems, and infrastructures by synchronizing local time to a unified network clock that has no single point of failure.

Professor Aggelos Kiayias, director of the Blockchain Technology Laboratory at the University of Edinburgh and Chief Scientist at Input Output, who led the research, says: 

The problem of synchronizing clocks without a central time-keeper is essential in creating a truly robust decentralized financial system. For the first time, we have developed a blockchain mechanism that enables a dynamically evolving group of parties to calibrate their local clocks so they are consistent â€“ even if they come and go following arbitrary participation patterns. By creating a blockchain-based global clock, we have also paved the way to a more secure, tamper-resistant time source with many possible external applications.

By enabling accurate timing and thus full traceability of all transactions, the scientific breakthrough also marks a major step towards creating fully auditable and fraud-proof financial systems.

To find out more, see the published research [here](https://eprint.iacr.org/2019/838.pdf).

*Thanks to Rachel Bruce, Jenny Corlett, Rod Alexander, and Christian Badertscher for their input and support in writing this post.*
