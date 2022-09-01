# How pledging will keep Cardano healthy
### **Warding off attacks on the decentralized blockchain is just one benefit of the process**
![](img/2020-05-12-how-pledging-encourages-a-healthy-decentralized-cardano-ecosystem.002.png) 12 May 2020![](img/2020-05-12-how-pledging-encourages-a-healthy-decentralized-cardano-ecosystem.002.png)[ Lars Brünjes](tmp//en/blog/authors/lars-brunjes/page-1/)![](img/2020-05-12-how-pledging-encourages-a-healthy-decentralized-cardano-ecosystem.003.png) 5 mins read

![Lars Brünjes](img/2020-05-12-how-pledging-encourages-a-healthy-decentralized-cardano-ecosystem.004.png)[](tmp//en/blog/authors/lars-brunjes/page-1/)
### [**Lars Brünjes**](tmp//en/blog/authors/lars-brunjes/page-1/)
Education Director

Education

- ![](img/2020-05-12-how-pledging-encourages-a-healthy-decentralized-cardano-ecosystem.005.png)[](mailto:lars.bruenjes@iohk.io "Email")
- ![](img/2020-05-12-how-pledging-encourages-a-healthy-decentralized-cardano-ecosystem.006.png)[](https://www.linkedin.com/in/dr-lars-br%C3%BCnjes-1640993b "LinkedIn")
- ![](img/2020-05-12-how-pledging-encourages-a-healthy-decentralized-cardano-ecosystem.007.png)[](https://twitter.com/LarsBrunjes "Twitter")
- ![](img/2020-05-12-how-pledging-encourages-a-healthy-decentralized-cardano-ecosystem.008.png)[](https://github.com/brunjlar "GitHub")

![How pledging will keep Cardano healthy](img/2020-05-12-how-pledging-encourages-a-healthy-decentralized-cardano-ecosystem.009.jpeg)

As we approach Shelley on the Cardano mainnet, decentralization has, inevitably, become a topic of debate. Regardless of any initial founding intent, proof-of-work cryptocurrencies such as Bitcoin and Ethereum have become more centralized over time. The early days of Bitcoin enthusiasts mining blocks at the weekend are long gone and today we see a small group of specialized, professional mining operations dominating their respective chains.

In itself, this isn’t necessarily a bad thing – but if it happened to Cardano, it would run contrary to the vision of a decentralized, proof-of-stake protocol. 

Cardano has been designed from the ground up with decentralization at its core and, in particular, in its stake delegation and reward mechanisms. On the Cardano network, pools above a certain size will not be competitive, and delegation rewards for everyone are optimal when there are many medium-sized pools. Every ecosystem benefits from diversity. Similarly, we believe that this approach offers the best balance between encouraging grass-roots involvement from skilled members of the community through to supporting those aiming to establish commercial stake pool businesses.
### **Pledging, and how it works**
During pool registration, a pool operator can choose to pledge some personal stake to their pool to make the pool more attractive. The pledged amount can be changed on an epoch-by-epoch basis and will be returned when the pool is closed.

Everybody can operate a pool on the Cardano blockchain. No minimum pledge is required. Pool operators can optionally pledge some or all of their stake (or the stake of their friends and partners) to their pool to make their pool more attractive. The higher the amount of ada pledged, the more rewards the pool will receive, which will attract more delegation.

It is important to remember that there is also no maximum pledge, so a pool operator with a lot of ada to stake can maximize their own rewards by saturating the pool with the pledge and not attracting any delegation. This will of course only be possible for very few operators; most operators will try to attract delegation with a combination of pledge, low costs, low margin and good performance.

How attractive a pool is to delegators depends on four interacting elements:

- operating costs (the lower, the better); 
- operator margin (the lower, the better);
- performance (the higher, the better);
- level of pledge (the higher, the better). 

By pledging more, the pool operator can ask for a higher operator margin while still being attractive to delegators.
### **Why is pledging necessary?**
Pledging provides a mechanism to encourage a healthy commercial ecosystem on the Cardano blockchain. The pledging mechanism is also necessary to protect the system against Sybil attacks. As I've discussed before, in a [Sybil attack](https://iohk.io/en/blog/posts/2018/10/29/preventing-sybil-attacks/), someone with very little personal stake creates hundreds of pools with low margins and tries to attract the majority of stake to their pools. If this succeeds, they can control consensus and engage in double-spending attacks, create forks, censor blocks, and damage or even destroy the system. 

By making pools with higher pledges more attractive, such attacks are prevented, because an attacker now needs to split their stake between many pools, making those pools less attractive and increasing the inherent cost of attempting a Sybil attack.
### **How influential will pledging be?**
We face a classic trade-off here: we want the system to be as decentralized as possible and we want to give as many people as possible the chance to operate a stake pool, so pledging should not have a big effect on rewards.

On the other hand, we need to protect the system from Sybil attacks, and the higher the influence of pledging is, the more ada an attacker requires to succeed in such an attack.

The goal is clear: we want to set the influence of pledging as low as possible, while still being able to guarantee security. 
### **How do we determine the influence of pledging?**
The parameter that determines the influence of pledging will need to be set before the rollout of Shelley on the Cardano mainnet. However, the parameter has been designed to be flexible and adjustable over time. The [Shelley Haskell testnet](https://iohk.io/en/blog/posts/2020/04/29/from-byron-to-shelley-part-one-the-testnets/) will provide an ideal opportunity to tune this parameter and test which values work and which do not. We’re also developing a calculator to help pool operators model different pledge amounts and work out how this might affect delegation and thus their rewards and revenues.

Reasonable values depend on many factors: How much stake does a typical pool operator own? How expensive is it to operate a node? How many people are interested in operating a pool? We gathered a lot of data during the Incentivized Testnet, and we will gain even more from the next testnet in close collaboration with our users. 

We believe in our scientific approach and are confident that our design will lead to a decentralized, stable, and secure system – but science and mathematics only get you so far. You always have to make modeling assumptions, and no model can ever be as complex and colorful as the real world and the real people who make up the Cardano community. 

We have already seen some very positive contributions and debate on the topic, including on [Reddit](https://www.reddit.com/r/cardano/comments/gfed1l/cardano_mainnet_pledge_influence_factor_analysis/) and a recent [Cardano Effect](https://www.youtube.com/watch?v=ubWIytFZYGE) show. The Shelley Haskell testnets will be the perfect training ground for us to continue to debate, assess and iterate, collaborating with stake pool operators to see what is optimal for everyone. Just as we saw with the success of the Incentivized Testnet and the recently launched [Daedalus Flight user testing](https://iohk.io/en/blog/posts/2020/04/01/we-need-you-for-the-daedalus-flight-testing-program/), it’s again the time to draw upon the community’s help to put our research into practice.
