# Bringing Glow to Cardano
### **We just spun up a devnet to support Glow, the very latest language Cardano will support. We talked to its creator about building a DSL for DApp development.**
![](img/2021-02-26-bringing-glow-to-cardano.002.png) 26 February 2021![](img/2021-02-26-bringing-glow-to-cardano.002.png)[ Eric Czuleger](tmp//en/blog/authors/eric-czuleger/page-1/)![](img/2021-02-26-bringing-glow-to-cardano.003.png) 7 mins read

![Eric Czuleger](img/2021-02-26-bringing-glow-to-cardano.004.png)[](tmp//en/blog/authors/eric-czuleger/page-1/)
### [**Eric Czuleger**](tmp//en/blog/authors/eric-czuleger/page-1/)
Senior Content Editor

Marketing & Communications

- ![](img/2021-02-26-bringing-glow-to-cardano.005.png)[](mailto:eric.czuleger@iohk.io "Email")
- ![](img/2021-02-26-bringing-glow-to-cardano.006.png)[](https://www.linkedin.com/in/eric-czuleger-6b67a395/ "LinkedIn")
- ![](img/2021-02-26-bringing-glow-to-cardano.007.png)[](https://twitter.com/eczuleger "Twitter")

![Bringing Glow to Cardano](img/2021-02-26-bringing-glow-to-cardano.008.jpeg)

*At the end of 2020, we announced our devnets plan to support the longer-term strategic goal of opening up Cardano to multiple development languages â€“ as outlined in the â€˜â€˜[Island, Ocean, Pond](https://youtu.be/k8a6tX53YPs)â€™ video. This week, building on the [Ethereum Virtual Machine](https://developers.cardano.org/en/virtual-machines/welcome/), weâ€™re rolling out a new [development environment](https://developers.cardano.org/en/programming-languages/glow/overview/) to support the Glow language.*

*FranÃ§ois-RenÃ© Rideau of Mutual Knowledge Systems is the creator of Glow, a DSL that will allow anyone to write verifiable DApps from a single spec and deploy it on our EVM network. We caught up with Rideau (also known as Fare) to hear more about his vision for Glow and the Cardano journey so far. The following is a distillation of his thoughts from our previous interviews.*

**We first introduced the community to GLOW and MuKn at the end of [last year](https://youtu.be/lj9SlvOIBgU?t=2902) when we announced our devnets approach â€“Â  but maybe you can remind us how you began working with IOHK?**

I started as a researcher in formal methods for programming languages and distributed systems. But I wanted to build systems actually used by many, so I moved into the industry where I notably worked on proving the correctness of a centralized payment protocol and creating an airline reservation system. After a few years at Google and Bridgewater, I decided life wasnâ€™t worth working under dysfunctional hierarchies, so I started my own cryptocurrency companies. Charles invited me to speak at the IOHK Summit 2019, and I realized how much I like the Cardano community: we have a similar focus on building robust software for the long term. That is why I wanted to port my domain specific language Glow to Cardano.

**Tell us a bit why you started your company Mutual Knowledge Systems, or as you call it MuKn (Moon)?**

Over three years ago, I was reviewing whitepapers. Most papers (about Â¾) had interesting techniques but made no economic sense. Most of the rest (about â…•) made economic sense but had no technical content. Only the top few (about 5%) actually made sense both technically and economically. At some point, I realized I could do better, so I designed a scaling solution using lessons learned from working on Tezos. Arthur Breitman challenged me to use smart contracts instead of trying to modify his protocol. 

While trying to prove his challenge absurd, I instead found that he was right and I was wrongâ€”and I finally understood why and how to use smart contracts. I started a company around the resulting scaling solution, raised money, pivoted into building the scaling solution after the language capable of generating it from specification, fought with and fired my then-partner, became my own CEO, started a new company, and, after much struggle, finally found the right founding team. Together, we built Mutual Knowledge Systems around this new programming language, Glowâ€”designed to be much better than existing languages to write decentralized applications.

**When you say â€˜betterâ€™, what do you really mean?**

Writing a DApp is the single hardest thing to do in the world. This is because you canâ€™t afford a mistake, or your users may lose significant funds. Furthermore, you are not confronting random situations, but active adversaries bent on attacking your code, who will contrive the very worst case scenarios to exploit for their profit. Yet, unlike the military, you canâ€™t hide your code or protect access to your networks: all the critical pieces are necessarily public. On top of that, extant programming tools are not designed for these constraints and even traditional formal methods lack essential concepts to express the issues at stake.

Thus, we decided to make new tools fit for the challenge. Our domain-specific language (DSL) drastically simplifies DApp development, by abstracting away all the common blockchain infrastructure, so you can focus on your problem domain (trading, derivatives, insurance, supply chain, etc.). Your DApps can be thousands of lines of code that your users can afford to audit, instead of millions of lines of code that require leaps of blind faith. And the programming model will enable developers, auditors and automated verification tools to reason at the level of abstraction of participants exchanging assets, rather than at that of packets of bytes shipped around the Internet.

**What is it about Cardano and its community that appeals?**

I started like everyone else, on Ethereum, because its ecosystem is already mature. However, the Ethereum community has this attitude of building as fast as possible experiments that are good enough for now, but lack conceptual integrity and wonâ€™t last; I see a lot of value in that approach and have tremendous respect for those who can thrive this wayâ€”for I cannot. When I met the Cardano community, I felt much more at home because we share a common attitude. We want to do things that are correct by construction and will keep working in the long term. We build concrete towers on the bedrock, not stick shacks on the sand. At times, this can be frustrating because things go slow, but I am happy with the attention to detail and quality in the development of Cardano. Is it perfect? No, itâ€™s not. But itâ€™s got great fundamentals.

**Can you talk about how you hope Glow will change the DApp developer experience?**

Glow is portable. Today it works on Cardano and Ethereum but in the future it will work with any blockchain that is sufficiently advanced to support smart contracts. That means that you can write your DApp once and it will run on whichever platform has the users and the liquidity you seek. You donâ€™t have to make a guess about where liquidity will be in the future then sink heavy investments to develop on a single chain that you bet your house on.

With Glow, developers can run their DApps on all blockchains. Glow will commoditize blockchains. Blockchains will then compete on technical and economic merits, not on user lock-in and inertia. And the value brought to users will increase.

**What can the community expect from Glow?**

We have launched this early version of Glow on the Cardano EVM Devnet with a command-line interface. In many ways, it is not yet ready for use by end-users, but it can already demonstrate simple applications. Users can also see how they may write a 6 line application in Glow that would require hundreds of lines in a combination of Solidity and JavaScript. We have a roadmap over the next few months to add a lot of features: from ERC20 tokens (and, on Cardano, native tokens), to generalized state channels, to a web interface, to a more robust runtime, etc. Eventually, we want to become the development environment for all blockchain projects. And Glow is of course an open source software open to the community.

**Weâ€™re rolling out the integration with Glow with our EVM and devnet program, so what are some of the benefits of this?**

The Cardano EVM side-chain will enable arbitrary contracts to run on Cardano that use the mature EVM platform, without waiting for Plutus to deliver its promise, to achieve feature-parity, to be considered stable, etc. And Glow can run on this EVM side-chain and provide the simplicity, safety and portability in DApp development that were not available before.

**What is the rollout process like and how can our community get involved if they want to?**

Glow is still in development. There are some things that it can do already and some it canâ€™t do yet. We invite DApp developers to join the Glow community and use the language for what it can already do, and otherwise help us build the blockchain development environment of the future. You can build the missing features you need yourself, or contract MuKn to build them for you. Even if you canâ€™t code and have no budget, you can help write the documentation, or even just tell us where it isnâ€™t clear yet, or what features you need most so we know what to prioritize. Together, we can build great DApps that you just couldnâ€™t have achieved safely and within budget with previous tools.

*If youâ€™re a developer, we encourage you to get involved with [Mutual Knowledge Systems and Glow](https://mukn.io/). See our full conversation with FranÃ§ois-RenÃ© Rideau and a demonstration of Glow during [Cardano360.*](https://youtu.be/YXaK0cvgoFQ?t=4367)*
