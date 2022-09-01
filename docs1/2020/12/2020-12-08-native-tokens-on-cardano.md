# Native tokens on Cardano
### **The Cardano ledger will handle tokenized assets natively – there’s no need for any custom code. In the first of a two-part post, we’ll look at Cardano’s approach to tokenization through native tokens, why native assets are necessary, and their advantages over ERC-20 and ERC-721 tokens**
![](img/2020-12-08-native-tokens-on-cardano.002.png) 8 December 2020![](img/2020-12-08-native-tokens-on-cardano.002.png)[ Tim Harrison](tmp//en/blog/authors/tim-harrison/page-1/)![](img/2020-12-08-native-tokens-on-cardano.003.png) 6 mins read

![Tim Harrison](img/2020-12-08-native-tokens-on-cardano.004.png)[](tmp//en/blog/authors/tim-harrison/page-1/)
### [**Tim Harrison**](tmp//en/blog/authors/tim-harrison/page-1/)
VP of Community & Ecosystem

Communications

- ![](img/2020-12-08-native-tokens-on-cardano.005.png)[](mailto:tim.harrison@iohk.io "Email")
- ![](img/2020-12-08-native-tokens-on-cardano.006.png)[](https://uk.linkedin.com/in/timbharrison "LinkedIn")
- ![](img/2020-12-08-native-tokens-on-cardano.007.png)[](https://twitter.com/timbharrison "Twitter")
- ![](img/2020-12-08-native-tokens-on-cardano.008.png)[](https://github.com/timbharrison "GitHub")

![Native tokens on Cardano](img/2020-12-08-native-tokens-on-cardano.009.jpeg)

Your browser does not support the audio element.

It all began in the ether. Ethereum was launched in July of 2015. Bitcoin had been around for six years by then, but the whole cryptocurrency world still remained a niche affair. 

Bitcoin was designed (and so it remains today) purely as a digital currency. When Ethereum came along, it had a solid ace up its crypto sleeve: smart contracts, right out of the box. This meant that third-party developers could build their own applications and run them in a decentralized manner on top of the Ethereum blockchain. Ethereum trumped Bitcoin with better marketability and more versatility. 

Smart contracts enabled the creation of user-defined tokens on the Ethereum blockchain. Fungible Ethereum tokens could be developed with the ERC-20 standard, while unique, non-fungible tokens were created under the ERC-721 framework. However, user-defined Ethereum tokens (both fungible and non-fungible) carried an inherent inefficiency: they required the creation and implementation of custom code because the Ethereum chain did not offer native token support.
### **Tokenization in brief**
Let’s remind ourselves of the purpose and value of tokens. Tokenization can be defined as the process of substituting a sensitive data element with a non-sensitive equivalent. This non-sensitive equivalent is referred to as a token and it has no extrinsic or exploitable meaning or value. Simply put, tokenization is the process of turning things into digital assets.

This approach offers distinct advantages: reduced transaction costs, transparency, enhanced liquidity, decentralization, and increased efficiency, to name a few. In itself, tokenization is a highly versatile feature that opens the path to achieving many commercial objectives. This utility stems from the fact that tokens are programmable, so they can be made unique.

For example, tokens can be programmed to grant the holder access to exclusive content, custom merchandise, or even a stake in voting. The actual purpose of the voting process is irrelevant. Ultimately, tokenizing the ability to vote gives participants the feeling that they are part of something larger than themselves, and they can have their views represented in it.

Tokenization can be used to create financial products and economic models. Examples can be envisaged in fields as diverse as collectibles, alternative investments, gift cards, sports betting, in-game assets, commodities, and much more. This has the potential to connect real world goods, services, and activities to the digital space.
### **Turning things into digital assets, the Cardano way**
Goguen introduces a mechanism whereby tokenization is handled natively. That is, the logic is based on the Cardano ledger, rather than smart contracts. By taking this approach, we are able to implement an efficient tokenization strategy that is superior to the ERC-20 and ERC-721 standards supported on the Ethereum blockchain. 

User-defined tokens on the Ethereum chain (both fungible ERC-20 and non-fungible ERC-721 tokens) are non-native, that is, the underlying ledger does not directly support these tokens. That is because tokens created with ERC-20 and ERC-721 standards are fundamentally different from Ether, the cryptocurrency native to Ethereum. 

The Cardano approach to tokenization enables the representation of custom assets on the blockchain without the need for smart contracts, and also enables those assets to behave in a similar way to the principal currency, ada, except that:

- native tokens can be created and destroyed, unlike ada. 
- ada is the only currency that can be used to service fees, rewards, and deposits.
### **Native tokens, some terminology**
The terms 'coin' and 'token' are often used in the crypto world. Sometimes, these terms are interchangeable, sometimes not. And sometimes, 'token' is a sort of umbrella term that encompasses all digital assets.

It is worth making a finer point here. Cardano's approach to tokenization is as unique as the ledger itself, so here's some terminology to help understand the native tokens framework. 

In Goguen/Cardano:

- A token is defined as the representation of an asset stored on the Cardano blockchain
- An asset is anything that can be quantified
- A token bundle is a representation of multiple tokens
- Native refers to token logic running on the Cardano ledger, rather than using smart contracts. 
### **Native tokens on Cardano**
Ethereum requires custom code for user-defined tokens to be supported on the chain; this adds a layer of complexity, cost (gas is needed to pay for the execution of the code), and inefficiency, since token code for both standards is replicated and adapted, rather than being part of the system itself. This is an inherent weakness of the Ethereum chain, because it leaves room for human error. Custom code, if done sloppily, can introduce bugs that could potentially lead to great financial loss.[In one particularly infamous incident](https://www.theguardian.com/technology/2017/nov/08/cryptocurrency-300m-dollars-stolen-bug-ether), software bugs led to the loss of ether worth $300m. The Cardano approach aims to prevent such catastrophic errors.

Cardano supports user-defined tokens natively, that is, without the need for custom code, through the native tokens framework. Native tokens is an accounting system defined as part of the cryptocurrency ledger and enables tokens to be transacted with (tracked, sent and received.) This eliminates the need to use custom code or costly smart contracts. In short, native tokens remove the unnecessary layer of expensive complexity and inherent inefficiency found in the Ethereum chain.
### **Why are native assets necessary on Cardano?**
Cardano is a distributed ledger. Typically, when a distributed ledger is designed, it can only track a single asset type (its own cryptocurrency, for example.) But as the ledger evolves in terms of further decentralization, the need and possibility of tracking multiple types of assets using the same infrastructure becomes apparent, which is why many blockchains can support multiple assets such as stablecoins, utility tokens, credential tokens, and security tokens.

Native token functionality extends the accounting infrastructure defined in the ledger model (which is designed for processing ada-only transactions) to accommodate transactions that use different types of assets simultaneously.

*Native tokens on Cardano have advantages over ERC-20 and ERC-721 tokens, in terms of security and affordability. In the next blog post, to be published tomorrow, we’ll dig down into this as well as outline how developers can get involved in the months ahead. For now, visit our [Cardano documentation site](https://docs.cardano.org/native-tokens/learn), where you can access supporting documentation and resources.*
