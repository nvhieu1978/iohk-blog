# Devnets: Building bridges to developer communities
### **Our new interoperability platforms (devnets) will expand Cardano's reach with support for the Solidity/Ethereum communities and beyond**
![](img/2020-12-17-devnets-building-bridges-to-developer-communities.002.png) 17 December 2020![](img/2020-12-17-devnets-building-bridges-to-developer-communities.002.png)[ Tim Harrison](tmp//en/blog/authors/tim-harrison/page-1/)![](img/2020-12-17-devnets-building-bridges-to-developer-communities.003.png) 6 mins read

![Tim Harrison](img/2020-12-17-devnets-building-bridges-to-developer-communities.004.png)[](tmp//en/blog/authors/tim-harrison/page-1/)
### [**Tim Harrison**](tmp//en/blog/authors/tim-harrison/page-1/)
VP of Community & Ecosystem

Communications

- ![](img/2020-12-17-devnets-building-bridges-to-developer-communities.005.png)[](mailto:tim.harrison@iohk.io "Email")
- ![](img/2020-12-17-devnets-building-bridges-to-developer-communities.006.png)[](https://uk.linkedin.com/in/timbharrison "LinkedIn")
- ![](img/2020-12-17-devnets-building-bridges-to-developer-communities.007.png)[](https://twitter.com/timbharrison "Twitter")
- ![](img/2020-12-17-devnets-building-bridges-to-developer-communities.008.png)[](https://github.com/timbharrison "GitHub")

![Devnets: Building bridges to developer communities](img/2020-12-17-devnets-building-bridges-to-developer-communities.009.jpeg)

Your browser does not support the audio element.

A blockchain environment is not a static one. Blockchains evolve as their communities grow and learn, and Cardano is no exception. 

With every development stage, Cardano's core functionality has been expanded with new features: Shelley added delegation, stake pools, and decentralization to Byronâ€™s core transactional capability. Goguen is now starting to bring fresh utility, from metadata to smart contracts and native tokens. Voltaire introduces a treasury and voting system, and weâ€™ve seen the early steps of this process with Project Catalyst and the first ever public funding round for Cardano community ideas.

We introduced transaction metadata in November, an important first element in creating new utility and commercial use cases. We recently deployed the first pre-production environment for native tokens. Following that will be token creation and ERC-20 conversion. Plutus and Marlowe, Cardanoâ€™s native smart contract languages are under active development and will be released in 2021, opening up the platform for developers to create fresh solutions and power exciting new use cases. 

All of these Goguen elements play their part in delivering Cardano's ultimate objective: a truly decentralized and self-sustaining platform. All the time encouraging deeper community engagement and growth by creating fresh opportunities. 

We have a vibrant and skilled community, arguably one of the strongest and smartest in the crypto space. And in line with our avowedly non-â€™maximalistâ€™ and open approach, we want to reach out to other communities and bring them onboard too.

As outlined in [Charles Hoskinsonâ€™s recent video](https://www.youtube.com/watch?v=k8a6tX53YPs), Cardano's next strategic move will be the addition of a range of devnets to draw fresh developer communities into the wider Cardano ecosystem.

These devnets will act as â€˜bridgesâ€™ between developer communities, providing development environments, virtual machines and suites of developer tools so new applications can be tested in an environment as close to the 'real world' as possible.
### **Understanding the devnets**
After some initial exploratory work back in 2018, we are now restarting and accelerating the K Ethereum Virtual Machine (KEVM) program. The new [KEVM devnet](https://developers.cardano.org/en/virtual-machines/kevm/overview/) is the first of several devnets weâ€™re building out over the next month or so. The EVM runs within the K Framework, a system for specifying languages and VMs, and then deriving tools such as interpreters, type checkers, equivalence checkers, debuggers, etc. for these languages. (The EVM is what runs smart contracts in the Ethereum network.)

K applies formal reasoning and mathematical rigor for the highest levels of assurance. It enables developers to define or implement the formal semantics of a programming language in an intuitive and modular way. K also generates an executable, 'correct by construction VM' from its formal specification, which is fast and powerful enough to run real programs and smart contracts. This effectively means that software should perform the required functions and *nothing else*, for all possible inputs, and have verifiable evidence. 

Our long term vision â€“ in association with our partners at Runtime Verification â€“ is to build a K environment where we can just 'plug-and-play' new VMs. You can hear more about the goals of K from the team at Runtime Verification in [this video segment](https://youtu.be/lj9SlvOIBgU?t=1628) from the Cardano monthly show.

The KEVM devnet, which is aimed at the Solidity/Ethereum community, will enable full backward compatibility with Ethereum. Because Solidity is a high-level language similar to JavaScript and C++, it cannot be directly executed by the EVM. Solidity programs must be compiled to assembly language (EVM bytecode) first, so they can run on the KEVM. 

KEVM will allow developers to write applications in Solidity, EVM code, or [Glow](https://www.youtube.com/watch?v=jWyBjjgdWWU), providing toolkits to compile and deploy them on the devnet for (close to real-world) testing. We also plan to soon add [Truffle](https://www.trufflesuite.com/docs/truffle/overview) integration, further increasing developer usability.
### **Glow**
Solidity is by far the most popular higher programming language compiling to EVM bytecode, but by no means the only one. One fascinating alternative to Solidity is Glow, developed by our partner MuKn.

Glow is a â€˜high-levelâ€™ language (other examples of high level languages include JavaScript, Python etc.) designed to allow writing highly secure financial contracts intuitively. Glow follows the 'correct-by-construction' doctrine to avoid common pitfalls and potentially costly bugs. Glow can prove that contracts written in this language have certain desirable properties, no matter what other participants in the contract do or do not do.

Glow has been designed with interoperability in mind. There will be Glow compilers targeting many diverse platforms and blockchains, making code reuse so much simpler and more practicable.

This will be the next devnet to be deployed. Most of the core development work is now done, ready for final QA and deployment in January 2021.
### **IELE - A foundation for third-generation blockchains**
Full compatibility with the EVM is convenient and attractive to many experienced developers familiar with Ethereum, but KEVM inevitably also inherits the EVMâ€™s weaknesses.

For this reason weâ€™ll offer a more advanced and secure alternative in the form of our IELE devnet. The IELE (pronounced *yeah-leh*) virtual machine, also being developed by our partner Runtime Verification, is similar to the EVM, but much more secure. For example, it uses arbitrary precision integers, immediately eliminating many of the EVM's vulnerabilities. IELE is also register-based, not stack-based like the EVM, making it much easier for developers to write IELE bytecode by hand directly.

The term IELE describes two things:

- The IELE VM
- The IELE assembly language

IELE is a human-readable, blockchain low-level language, meant to serve as the foundation for third-generation blockchains. IELE was designed using state-of-the-art formal methods to address security and correctness concerns in Ethereum, while simultaneously enabling the verification of mathematical correctness of smart contract code that K EVM brings to Ethereum. 

IELE represents the next step in the evolution of correct-by-construction, automatically generated implementation concepts. It is built to become the foundation of an entire compiler backend, allowing robust gas optimization, including contracts written in a high-level language that has IELE as its compilation target, like Solidity or Plutus.
### **Bridges between developer communities**
The KEVM, Glow and IELE devnets align closely with Goguenâ€™s key goals: to bring use and utility to Cardano, and build solid, lasting partnerships that contribute to the ongoing growth of our developer ecosystem. We aim to attract as many developers from as many disciplines as possible, to foster versatility and inclusivity.

Alongside Plutus and Marlowe, we hope these devnets present an unrivalled opportunity for developers (in the blockchain-crypto world and beyond) to engage with the Cardano platform, build compelling use cases, and contribute to the growth of the ecosystem.
### **An exciting future**
We hope to provide a clear path towards new developer opportunities that will require close collaboration with many different communities, not least Cardanoâ€™s own. And it's one step at a time. 

Weâ€™re putting the building blocks in place now. Once fully established, the devnets will act as bridges between developer communities, opening up new avenues of communication and cooperation across not just blockchain, but the whole developer ecosystem. Cardano will have permanent backward compatibility with the Ethereum network, keeping pace with any developments in the Ethereum chain. And by broadening the developer base, the Cardano community can help drive the continuing evolution of smart contracts and the decentralized finance (DeFi) space. Another remarkable year awaits. See you on the other side.
