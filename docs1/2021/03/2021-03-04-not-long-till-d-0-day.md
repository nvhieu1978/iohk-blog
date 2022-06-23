# Not long till 'd' (=0) day
### **We are fast approaching full decentralization of block production on Cardano. It's a good time to reflect on the network’s evolution**
![](img/2021-03-04-not-long-till-d-0-day.002.png) 4 March 2021![](img/2021-03-04-not-long-till-d-0-day.002.png)[ Colin L Edwards](tmp//en/blog/authors/colin-edwards/page-1/)![](img/2021-03-04-not-long-till-d-0-day.003.png) 8 mins read

![Colin L Edwards](img/2021-03-04-not-long-till-d-0-day.004.png)[](tmp//en/blog/authors/colin-edwards/page-1/)
### [**Colin L Edwards**](tmp//en/blog/authors/colin-edwards/page-1/)
Quantitative Strategist

Commercial

- ![](img/2021-03-04-not-long-till-d-0-day.005.png)[](mailto:colin.edwards@iohk.io "Email")
- ![](img/2021-03-04-not-long-till-d-0-day.006.png)[](https://www.linkedin.com/in/colin-edwards-04938a5/ "LinkedIn")

![Not long till 'd' (=0) day](img/2021-03-04-not-long-till-d-0-day.007.jpeg)

At the end of March, we’ll reach another milestone for Cardano when we’ll see *d*, the parameter that governs what percentage of transactions are processed by the genesis nodes, get to zero. At this point, responsibility for block generation will be fully decentralized. In other words, Cardano’s network of 1,800+ community pools will be solely responsible for producing blocks.

*D*=0 day will be a landmark moment in Cardano's continuing journey. When we deployed the Shelley update back in July 2020, *d* was set to an initial 1.0, meaning that every block was produced by IOHK’s network of federated nodes. Of course, this was the antithesis of decentralization but a wise (ie, secure) approach for the near term while the stake pool operator (SPO) network got up and running. 
### **Preparing for *d*=0 day**
Over time, we have gradually reduced *d* at a rate of 0.02 per epoch (in other words, an increase of two percentage points in community block production every five days). On the day this blog is published, we are at *d*=0.12 with 88% of blocks being produced by community pools and just 12% by federated nodes. 

Simply put, as *d* decreases, more blocks are created by the community, and more stake pools can produce blocks. As *d* ticks down, the network's diversity and geographic distribution expands.

On March 31, at the boundary of epoch 257, *d* will reach zero. That day will be special because while *d* may be small, its significance is huge. In this context, that zero heralds the most important outward indicator of decentralization, a parameterized symbol supporting a core tenet of our philosophy – *d=0 pushes power to the edges*.

As we continue transitioning to full decentralization, it is also a good time to reference the other parameters governing the Cardano network’s evolution, and review some of the changes we have seen. 

The *d* number is just one of more than 20 parameters that govern network operation and health. This set of parameters are ‘levers’ to manage and steer the effective and natural operation of a [decentralized proof-of-stake system](https://iohk.io/en/blog/posts/2020/11/13/the-general-perspective-on-staking-in-cardano/). The community will ultimately drive Cardano's evolution via Voltaire governance rules, but until then, it's our job to manage this set of parameters. Our guardianship requires that we make adjustments as required to build and sustain the health of the network. 
### **Why the *k* parameter is special**
Aside from more technical considerations, we remain committed to supporting smaller stake pools, because we believe this approach aligns with our long-term goal of creating the most decentralized and economically sustainable ecosystem of stake pools. This is further reflected in our [delegation approach](https://iohk.io/en/blog/posts/2020/12/10/delegating-to-decentralize-and-build-value/), which throughout 2021 will aim to support stake pool diversity.

Last year, we made the first significant adjustment to network parameters when we moved *k* from 150 (meaning a system optimized at launch for 150 block-producing pools, even though other pools could produce blocks) to *k*=500. This came about after extensive debate, both within IOHK and the Cardano Foundation and with the SPO community.

The move to *k*=500 was a balanced decision based on the need to create opportunity for more pools to produce blocks (by encouraging the flow of stake from saturated pools into new pools), while supporting the pools already creating blocks, and minimizing disruption for their delegators. Overall, it has proven successful – let's dive a little deeper.
### **The change to *k*=500**
Prior to the announcement that *k* was changing, 54.6% of all delegated ada was represented by the 10 largest stake pools and 45.4% of ada represented by smaller pools. Following the change to *k*=500, those numbers have reversed: 55.9% of ada is now represented by pools other than the 10 largest.

![](img/2021-03-04-not-long-till-d-0-day.008.png)

This was a dramatic change directly linked to the change in *k*.

![](img/2021-03-04-not-long-till-d-0-day.009.png)

It is a great start, but our goal is to continue to optimize the network. So we observed what happened, gathered feedback, and incorporated everything we learned into making the next round of changes. 

Pools will split when it makes economic sense to do so. For those pools with a greater proportion of pledge, the more pledge they have, the more valuable it is and the more reason SPOs have to keep their pledge together. Conversely, if a pool has a low level of pledge, there is very little reason not to split it further to start additional pools.

While there is a cost associated with running a small pool, and given the current appreciation in the value of ada, we believe that the financial incentive for splitting pledge is even stronger now. Increasing *k* – for example to 1,000 – without addressing this first, would not lead to a more distributed and diverse ecosystem which, to be clear, is the objective. We will simply see many of the same operators just running twice as many pools.
### **Changing pledge**
The *a0* parameter rewards SPOs for concentrating their pledge into a small number of pools. This has been effective in encouraging pools with high levels of ada pledge to consolidate that into large private pools (as we at IOHK do) and therefore give smaller pools greater opportunity to attract delegation. 

However, we believe the current system can be improved, so for some time now, we have been discussing and modeling options to make pledge more effective at addressing pool splitting for lower pledge levels. 

The current structure of the rewards formula does not give us the flexibility to tweak the impact by a simple parameter change; we will need to modify the rewards formula, which is something our research team has been working on for some time. 

Several promising candidates have come out of that evaluation process. We’d like at this point to acknowledge the valuable work from community contributor Shawn McMurdo in his [Curve Pledge Benefit improvement proposal](https://github.com/cardano-foundation/CIPs/pull/12) for helping to develop the thinking in this area.

Our research team is in the late stages of finalizing an approach. They will soon present their findings, and we will update the community then. However, the team has now concluded that *a0* should change. We believe this change will greatly benefit the network, making the system more sustainable, widely distributed, and globally diverse. It will also increase the earnings of all public pools (ie, those that are not already fully 'saturated' with pledge).

While it has been a matter of considerable internal discussion, we have also concluded that any change in *k* should come after changing the formula for *a0* to deliver the desired results (especially encouraging stake to flow to smaller single pools rather than split pools). Since this is a full formula modification, and no longer a simple epoch boundary change, it needs to be released as part of a hard fork. Given our product pipelines and the team’s current focus on continuing the Goguen rollout and available dates, we will be looking to making this change in the third quarter of the year.
### **Other considerations**
Other factors need to be considered. Chief among these is the availability of multi-pool delegation, to allow ada holders to spread their stake across a number of pools from a single wallet. This requires significant backend work from the core development team, along with a new interface and business rules adjustments. We would also like – if possible – to offer better pledging options for SPOs from Daedalus in a similar timeframe (currently only available via CLI or AdaLite), which means additional development work not only for internal teams but also for the Ledger and Trezor wallet companies. 

We will also continue researching other parameters such as the minimum fees (implemented to prevent a ‘race to the bottom’ yet skewed against smaller pools) while continuing benchmarking and optimizing node performance as smart contract functionality rolls out. Our responsibility and commitment remains to achieve a delicate balance between the stability, scalability and overall health of the network with a flourishing ecosystem of pool operators and delegators.
### **Evolving into the future**
As we promote the health of the network and stake pool ecosystem, we continue to monitor and research other important parameters and values. This work considers both the tactical and strategic approaches we may take.

With the increase in the price of ada, implementation of native tokens, and anticipating smart contracts, we also continue to assess and review the Cardano fee structure. For example, based on community feedback, we are considering the tactical approach of immediately lowering some fees. The minimum fixed fee of 340 ada for stake pools is one strong candidate for change; network transaction fees and deposits for smart contracts are also under discussion.

Our researchers and analysts are also working with an external economic consulting group to formalize an optimization approach that ensures fees will remain stable and predictable over the longer term. The results of this review will include a governance model with a clear mandate about when and how fees should be determined in the future as we develop, optimize and scale the network. We’ll be sure to keep the community informed and involved as our thinking develops.

*I’d like to thank and acknowledge Francisco Landino, Lars Brünjes, Aikaterini-Panagiota Stouka, Aggelos Kiayias, and Tim Harrison for additional input to this article and feedback throughout this evaluation period.*
