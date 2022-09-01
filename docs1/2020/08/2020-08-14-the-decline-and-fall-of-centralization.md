# The decline and fall of centralization
### **This week marks the first step in the road to the full decentralization of Cardano, as stake pools begin to take responsibility for block production. Here’s what the journey will look like.**
![](img/2020-08-14-the-decline-and-fall-of-centralization.002.png) 14 August 2020![](img/2020-08-14-the-decline-and-fall-of-centralization.002.png)[ Kevin Hammond](tmp//en/blog/authors/kevin-hammond/page-1/)![](img/2020-08-14-the-decline-and-fall-of-centralization.003.png) 12 mins read

![Kevin Hammond](img/2020-08-14-the-decline-and-fall-of-centralization.004.png)[](tmp//en/blog/authors/kevin-hammond/page-1/)
### [**Kevin Hammond**](tmp//en/blog/authors/kevin-hammond/page-1/)
Software Engineer

Engineering

- ![](img/2020-08-14-the-decline-and-fall-of-centralization.005.png)[](https://twitter.com/inputoutputhk "Twitter")

![The decline and fall of centralization](img/2020-08-14-the-decline-and-fall-of-centralization.006.jpeg)

Full decentralization lies at the heart of Cardano’s mission. While it is not the only goal that we're focused on, in many ways, it is a goal that will enable and accelerate almost every other. It is *integral* to where we want to go as a project.

It is also where the philosophical and technical grounding of the entire Cardano project meets its community, in very real and tangible ways. This is why we have done a lot of thinking on how to achieve decentralization effectively, safely, and with the health of the ecosystem front of mind.
### **Defining *decentralization***
Let’s start by explaining what we mean by *decentralization*. This is a word that is fraught with challenge, with several competing meanings prevalent in the blockchain community. 

For us, decentralization is both a destination and a journey. Shelley represents the first steps toward a fully decentralized state; from the static, federated approach of Byron to a fully democratic environment where the community not only runs the network, but is empowered and encouraged to take decisions through an on-chain framework of governance and voting.

True decentralization lies at the confluence of three essential components, working together in unison.

- **Networking** - where geographically distributed agents are linked together to provide a secure and robust blockchain platform.
- **Block production** - where the work of building and maintaining the blockchain is distributed across the network to a collection of cooperating stake pools.
- **Governance** - where decisions about the blockchain protocol and the evolution of Cardano are taken collectively by the community of Cardano stakeholders.

Only when all these factors exist within a single environment can true decentralization be said to have been achieved successfully.
### **Key parameters that affect decentralization**
Let's talk about *d*, maybe.

The *d*-parameter performs a pivotal role in controlling the decentralization of block production. Decentralization is a spectrum, of course, rather than an absolute. In simple terms, d controls ‘how’ decentralized the network is. For example, at one extreme, *d*=1 means that block production is fully centralized. In this state, IOG’s core nodes produce all the blocks. This was how Byron operated,

Conversely, once *d*=0, and decentralized governance is in place and on chain, ‘full’ decentralization will have been achieved. At this point, stake pool operators produce all the blocks (block production is 100% decentralized), the community makes all the decisions on future direction and development (governance is decentralized), and a healthy ecosystem of geographically distributed stake pools are connected into a coherent and effective network (the network is decentralized). We will have reached our decentralization goal.

The journey that *d* will take from 1 to 0 is a nuanced one that requires a careful balance between the action of the protocol and the reaction of the network and its community. Rather than declining instantly, *d* will go through a period of ‘constant decay’ where it is gradually decremented until it reaches 0. At this point Cardano will be fully decentralized. This gradual process will allow us to collect performance data and to monitor the state of the network as it progresses towards this all-important point. A parameter-driven approach will help provide the community with transparency and a level of predictability. Meanwhile, we’ll be monitoring the results carefully; there will always be socio-economic and market factors to consider once ‘in the wild’.
### **How will the d parameter change over time**
The evolution from 1 to 0 is relatively simple:

When *d*=1, all blocks are produced by IOG core nodes, running in Ouroboros Byzantine Fault Tolerance (OBFT) mode. No blocks are produced by stake pool operators (running in Ouroboros Praos mode). All rewards go to treasury.

When *d*=0, the reverse becomes true: every block will be produced by stake pools (running in Praos mode), and none by the IOG core nodes. All rewards go to stake pools, once the fixed treasury rate is taken.

In between these extremes, a fraction of the blocks will be produced by the core nodes, and a fraction by the stake pools. The precise amounts are determined by *d*. So when *d* reaches 0.7, for example, 70% of the blocks will be produced by the core nodes and 30% will be produced by stake pools. When *d* subsequently reaches 0.2, 20% of the blocks will be produced by the core nodes, and 80% by the stake pools. 

It is important to note that regardless of the percentage of blocks that are produced by the stake pools, however, once *d* < 1, all the rewards will go to stake pools in line with the stake that they hold (after the fixed treasury percentage is taken), and none to the core nodes. This means that IOG has absolutely no incentive to keep the *d* parameter high. In fact, when *d* reaches zero, IOG will be able to save the costs of running the core nodes, which are not insubstantial.

Like many other ada holders, IO Global is currently running a number of stake pools on the mainnet. As the creator of the Cardano platform, IO Global naturally has a significant stake in its success from fiscal, fiduciary, and security aspects, and this success will be built on a large number of effective and decentralized pools. As a commercial entity, IO needs to generate revenue from its stake, while recognizing the part it needs to play within an ecosystem of stake pools, helping to grow and maintain the health of the network as we move towards full decentralization. In the medium term, we will follow a private/public/community delegation approach, similar to that we adopted on the ITN, spreading our stake across both IOG and community pools. In the short term, however, we are running IOG pools on the mainnet, establishing a number of our own pools that can take some of the load from our core nodes. Using our stake and technical expertise to secure and stabilise the network is an important element at first, but one that will become less important as the *d* parameter decreases. The road to decentralization will offer many opportunities for pools of all sizes to establish themselves and thrive along the way.

![d-parameter diagram](img/2020-08-14-the-decline-and-fall-of-centralization.007.png)
### **The key milestones of the *d* journey**
***d*<1.0 (Move away from centralization)**

The first milestone happened on August 13 at the boundary of epoch 210 and 211 when the *d* parameter first dropped below 1.0. At this point, IOG's core nodes started to share the block production of blocks with community stake pools. This marks the beginning of the road to full decentralization. 

***d*=0.8 (Stake pools produce 20% of blocks)**

At 0.8, more pools (double the number compared to *d*=0.9) will get the opportunity to create blocks and establish themselves. At this level, pools won’t suffer in the rankings as long as they create one of the allocated blocks and get rewards. This way, we believe we can start growing the block-minting proportion of the network, at low network risk.

***d*<0.8 (Stake pool performance taken into account)**

The next major milestone will happen when *d* drops below 0.8. Below that level, each pool's performance will be taken into account when determining the rewards that it receives. Above that level, however, the pool’s performance is ignored. The reason for this is to avoid unfairness to pools when they are only expected to produce a few blocks. 

***d*<0.5 (Stake Pools Produce the Majority of Blocks)**

When *d* drops below 0.5, stake pools will produce the majority of blocks. The network will have reached a tipping point, where decentralization is inevitable.

Before taking this dramatic step, we will ensure that two critical features are in place: peer-to-peer (P2P) pool discovery and protocol changes to enable community voting. These will enable us to make the final push to full and true decentralization The recently announced [Project Catalyst program](https://iohk.io/en/blog/posts/2020/08/05/philosophy-of-governance/) was the first step in this, concurrent journey to full on-chain governance.

***d*=0 (Achieve Full Decentralization)**

As soon as the parameter reaches 0, the IOG core nodes will be permanently switched off.

IOG will continue to run its own stake pools that will produce blocks in line with the stake they attract, just like any other pools. But these will no longer have any special role in maintaining the Cardano network. It will also, of course, delegate a substantial amount of its stake to community pools. Simultaneously, the voting mechanism will be enabled, and it will no longer be possible to increase *d* and ‘re-centralize’ Cardano. 

At this point in time, we will have irrevocably entered a fully decentralized Cardano network. **Network + block production + on-chain governance = decentralization.**
### **Rate of constant decay**
The progressive decrement of *d* is known as *constant decay*. The gradual decrease will give us the chance to monitor the effects of each decrement on the network and to make adjustments where necessary. As the parameter decreases, more stake pools will also be able to make blocks, since the number of blocks that are made by the pools will increase, and less stake will then be required for each block that is made.

The key factors driving this decrease will be:

- The resilience and reliability of the network as a whole.
- The number of effective block-producing pools.
- The amount of the total stake that has been delegated.

Here’s our current thinking on what implementation might look like:

![Constant decay timeline](img/2020-08-14-the-decline-and-fall-of-centralization.007.png)

We will then likely pause before dropping the parameter below 0.5 to ensure that the two key conditions described above are met:

- The implementation of the new Peer-to-Peer pool discovery mechanism has been released and is successfully in use;
- We have successfully transitioned the first hard fork in the Shelley era, which will introduce the basis for community voting on protocol parameters, and other important protocol changes

We will resume the countdown to *d*=0 at a similar rate, pausing again if necessary before finally transitioning to *d*=0 in March 2021.
### **Other factors that affect decentralization: Saturation threshold**
A second parameter – *k* – is used to drive growth in the number of pools by encouraging delegators to spread their stake. By setting a cap on the amount of stake that earns rewards (the saturation threshold), new delegators are directed towards pools that have less stake. In ideal conditions, the network will stabilise towards the specific number of pools that have been targeted. In practice, we saw from the ITN that many more pools than this number were supported by the setting that we chose. 

The *k* parameter was set to 150 at the Shelley hard fork. This setting was chosen to balance the need to support a significant number of stake pools from the start of the Shelley era against the possibility that only a small number of effective pools would be set up by the community. In due course, it will be increased to reflect the substantial number of pools that have emerged in the Cardano ecosystem since the hard fork. This will spread stake, and so block production, among more pools. The overall goal in choosing the setting of the parameter will be to maximise the number of sustainable pools that the network can support, so creating a balanced ecosystem. In order to achieve this, a careful balance is required between opening up the opportunity to run a block-creating pool to as many pools as want to run the system, against the raw economics of running a pool (from bare metal servers, to cloud services, to people’s time), taking into account the rewards that can be earned from the actively delegated stake. Changing this parameter will therefore be done with a degree of caution and balance so that we ensure the long term success of a fully decentralized Cardano network. We’re now looking carefully at early pool data and doing some further modelling before making the next move. 
### ***d* and pool rewards**
Two questions remain: What is the effect of *d* on the rewards that a pool can earn, and can this parameter ever be increased?

Regarding rewards, as long as a pool produces at least one block, the value of the parameter has absolutely no effect on the rewards that a pool will earn – only on the number of blocks that are distributed to the pools. So if a pool has exactly 1% of the stake, it will earn precisely 1% of the total rewards, provided that it maintains its expected performance.

![d parameters and rewards](img/2020-08-14-the-decline-and-fall-of-centralization.008.png)

Finally, while *d* could in theory be increased, there would need to be a truly compelling reason to do so (a major protocol issue, or fundamental network security, for example.) We would never envision actually doing this in practice. Why? Simply because we want to smoothly and gradually reduce the parameter to 0 in order to achieve our objective of true decentralization. We’ll be making this journey carefully but with determination step by step. If each step is taken thoughtfully and with confidence, you should not need to retrace them? As *d* becomes 0, the centralized IO servers will be finally switched off, and Cardano will become a model of decentralized blockchain that others aspire to be.
### **Conclusion**
The decline of centralized entities coincides with Cardano's rise towards full and true decentralization. In the near future, the Cardano blockchain will be solely supported and operated by a strong community of stake pools whose best interest is the health and further development of the network.

This journey, which began with Shelley and the implementation of the *d* parameter, will take Cardano through a path of evolutionary stages in which the network will become progressively more and more decentralized, as *d* decays. The journey will only end when the blockchain enters a state of irrevocable decentralization, a moment in time that will see networking, block production, and governance operating in harmony within a single environment.
