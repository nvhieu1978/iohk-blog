# Bringing certified DApps to Cardano
### **We’ll unveil a new integrated approach at the Cardano Summit this weekend. Here’s a preview...**
![](img/2021-09-22-bringing-certified-dapps-to-cardano.002.png) 22 September 2021![](img/2021-09-22-bringing-certified-dapps-to-cardano.002.png)[ Shruti Appiah](tmp//en/blog/authors/shruti-appiah/page-1/)![](img/2021-09-22-bringing-certified-dapps-to-cardano.003.png) 6 mins read

![Shruti Appiah](img/2021-09-22-bringing-certified-dapps-to-cardano.004.png)[](tmp//en/blog/authors/shruti-appiah/page-1/)
### [**Shruti Appiah**](tmp//en/blog/authors/shruti-appiah/page-1/)
Head of Product

Engineering

- ![](img/2021-09-22-bringing-certified-dapps-to-cardano.005.png)[](https://www.linkedin.com/in/shrutiappiah/ "LinkedIn")
- ![](img/2021-09-22-bringing-certified-dapps-to-cardano.006.png)[](https://github.com/ShrutiAppiah "GitHub")

![Bringing certified DApps to Cardano](img/2021-09-22-bringing-certified-dapps-to-cardano.007.jpeg)

The Alonzo upgrade has enabled the deployment of smart contracts, decentralized applications (DApps), and other applications on top of Cardano. All this is hugely significant for Cardano, as it will open Cardano to a whole new developer community whose creative drive will boost Cardano's utility and adoption.

Any new application ecosystem presents an enticing smorgasbord of exploration. Equally, an emergent ecosystem faces two key challenges at the beginning: discovery and quality assurance. Users need to be able to find the products they want to engage with, and do so with the reassurance of a certain baseline level of quality. 

The influx of new, third-party applications also poses the inherent risk of inappropriate or malicious material, or content that it's simply not up to standard. So addressing discovery and quality assurance issues is key to early ecosystem growth.

We’ll offer a deeper dive into this important topic this weekend at the Cardano Summit. There, we shall introduce a certification program to assess applications developed on top of Cardano. And also those on the upcoming dAppStore we are developing.
### **DApp discovery on Cardano**
The dAppStore – and we’ll preview a prototype at the Summit – is where developers will be able to upload their DApps running on Cardano and make them available to others in the. The store will provide a trusted, and democratized environment for developers to publish their DApps without facing censorship.

The Plutus dAppStore specifically addresses two barriers to entry:

- There currently is no formal discovery process for a DApp. Almost all discovery happens through organic or word-of-mouth means, or through social media marketing
- For end users, there is no consolidated view of all DApps available in a given ecosystem

Users will be able to access the Plutus dAppStore using a web browser. Think of the Plutus dAppStore as a 'storefront' for Cardano. The store displays the range of things that you can do on Cardano. A certification program gives users assurance about the behavior of any apps that they use, through automated logic checks, manual smart contract auditing, and formal verification. 

Any DApp can exist on the store, whether certified or uncertified, but we will provide users with clear information about a particular DApp's certification status. The dAppStore seeks not to act as gatekeeper (or judge) but rather to provide a platform for transparent user assessment.
### **The crucial role of certification**
The dAppStore is a shopfront. But aside from community validation, it offers no ‘baked in’ assurance. So this is where the second element comes in. The role of our certification program is the prevention of code-level security vulnerabilities. We shall achieve this by deploying different levels of ‘defense’. 

There will be several tiers. At the simplest level, automated logic checks will enable us to detect certain types of malicious code. For example, these will be able to check if the contract does not contain a way for locked up funds to be recovered. In a well composed contract, locked funds need to be retrievable.

Beyond that, manual smart contract auditing will help us verify any DApp’s integrity. Ultimately full formal verification will test the mathematical model to prove that a smart contract satisfies the formal specification of its behavior.

Of course, any certification program is only as good as those who implement and run it. For this reason, we are partnering with some of the leading names in the functional programming space, who you will meet at the Summit.
### **Building on a secure foundation: Cardano itself**
This certification effort builds on a blockchain that already provides more assurance than others like bitcoin or Ethereum. For example, tokens are built into the architecture of Cardano itself, rather than having to be provided by contracts, such as ERC20 on Ethereum. This eliminates any issues created by copying and modifying a contract to implement a new token.

Looking at the foundation of the chain, the [Extended Unspent Transaction Output (eUTXO)](https://iohk.io/en/blog/posts/2021/03/11/cardanos-extended-utxo-accounting-model/) accounting model is a fundamentally simpler – and more secure – model for a blockchain. Smart contracts in Plutus are functional programs, and the simple and verifiable semantics of functional languages underpins what we do with both automated testing and formal verification. We want to build a more secure foundation than other chains. Plutus is a functional language.

Also, Marlowe, our special-purpose language for finance, guarantees certain properties by design. For example, no Marlowe contract will retain assets after the contract has terminated. That is a property built into Marlowe, which does not require extra checks to be enforced. Because of its design, Marlowe also allows tools to automatically check that contracts have certain good properties by verifying every possible execution of the contract, without having to run it; this is something that general Plutus contracts cannot do.
### **Certification in the context of the Alonzo hard fork**
At the Summit we’ll show examples of automated testing of smart contracts, which are components of DApps, rather than full DApps.

In the longer term, we would like to see user-designed tools, the deployment of those tools to the store, and the evolution of the Plutus dAppStore to include new features such as upvoting, reviews, and even Atala PRISM integration etc., giving users the opportunity to feed back on the range of DApps in the store.

Through our work on the Alonzo testnets, the Plutus Pioneer program, and of course Project Catalyst, we have already seen a host of projects starting to build on Cardano. As these projects start to come to market over the months ahead, user discovery and user trust in those DApps will be key. We are working with an open, decentralized ecosystem, so the usual rules of *caveat emptor* and ‘Do Your Own Research’ will of course continue to apply. But helping drive higher standards in certification and assurance will be key to accelerating the growth of a successful ecosystem on Cardano and ultimately, the widest possible user base. 
##### **Simon Thompson and Fernando Sanchez also contributed to this piece.**
*Join us at the Summit on 25-26 September to learn more about this exciting new initiative and see a demo of the dAppStore prototype.*
