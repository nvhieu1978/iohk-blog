# Building native tokens on Cardano for pleasure and profit
### **New capabilities will allow users to choose simple and powerful tools to bring their assets to life on Cardano** 
![](img/2021-02-18-building-native-tokens-on-cardano-for-pleasure-and-profit.002.png) 18 February 2021![](img/2021-02-18-building-native-tokens-on-cardano-for-pleasure-and-profit.002.png)[ Tim Harrison](tmp//en/blog/authors/tim-harrison/page-1/)![](img/2021-02-18-building-native-tokens-on-cardano-for-pleasure-and-profit.003.png) 9 mins read

![Tim Harrison](img/2021-02-18-building-native-tokens-on-cardano-for-pleasure-and-profit.004.png)[](tmp//en/blog/authors/tim-harrison/page-1/)
### [**Tim Harrison**](tmp//en/blog/authors/tim-harrison/page-1/)
VP of Community & Ecosystem

Communications

- ![](img/2021-02-18-building-native-tokens-on-cardano-for-pleasure-and-profit.005.png)[](mailto:tim.harrison@iohk.io "Email")
- ![](img/2021-02-18-building-native-tokens-on-cardano-for-pleasure-and-profit.006.png)[](https://uk.linkedin.com/in/timbharrison "LinkedIn")
- ![](img/2021-02-18-building-native-tokens-on-cardano-for-pleasure-and-profit.007.png)[](https://twitter.com/timbharrison "Twitter")
- ![](img/2021-02-18-building-native-tokens-on-cardano-for-pleasure-and-profit.008.png)[](https://github.com/timbharrison "GitHub")

![Building native tokens on Cardano for pleasure and profit](img/2021-02-18-building-native-tokens-on-cardano-for-pleasure-and-profit.009.jpeg)

With the â€˜Maryâ€™ protocol upgrade, which will be implemented using our [hard fork combinator](https://docs.cardano.org/en/latest/explore-cardano/what-is-a-hard-fork-combinator.html) technology, native tokens and multi-asset capability are coming to Cardano.

On February 3, we upgraded[the Cardano public testnet](https://iohk.io/en/blog/posts/2021/02/04/native-tokens-to-bring-new-utility-to-life-on-cardano/) to â€˜Maryâ€™ for final testing. We plan to deploy the Cardano update proposal to mainnet on February 24, which would therefore deploy ahead of the boundary of epoch 250 and take effect on March 1. If we need a few more days of testing, we'll deploy â€˜Maryâ€™ the following epoch instead, which will take a five-day period required for updates to take effect. â€˜Maryâ€™ has been successfully running on our testing environments for several weeks, so our confidence level remains high. As always, however, weâ€™ll follow a strict process (developed and honed over the previous Shelley and Allegra HFC events) to get this right.

Once the code is successfully deployed to mainnet, weâ€™ll release a new [Daedalus Flight ](https://iohk.io/en/blog/posts/2020/04/01/we-need-you-for-the-daedalus-flight-testing-program/)version for user testing, which will be our first Cardano wallet with integrated multi-asset capability. Once we are happy with wallet performance and usability, weâ€™ll deliver the Daedalus mainnet release bringing the full-fat native token experience to every Cardano user.
## **Why native tokens?**
Native tokens will bring multi-asset support to Cardano, allowing users to create uniquely defined (custom) tokens and carry out transactions with them directly on the Cardano blockchain. 

The use of tokens for financial operations is becoming ever more popular. It can cut costs at the same time as improving transparency, enhancing liquidity, and, of course, being independent of centralized entities such as big banks. Tokenization is the process of representing real assets (eg, fiat currencies, stocks, precious metals, and property) in a digital form, which can be used to create financial instruments for commercial activities. 

Cardano will provide many [tokenization options](https://iohk.io/en/blog/posts/2020/12/08/native-tokens-on-cardano/). With the â€˜Maryâ€™ upgrade, the ledgerâ€™s accounting infrastructure will process not only ada transactions but also transactions that simultaneously carry several asset types. Native support grants distinct advantages for developers as there is no need to create smart contracts to handle custom token creation or transactions. This means that the accounting ledger will track the ownership and transfer of assets instead, removing extra complexity and potential for manual errors, while ensuring significant cost efficiency. 

**Future and utility**

Developers, businesses, and applications can create general purpose (fungible) or specialized (non-fungible) tokens to achieve commercial or business objectives. These might include the creation of custom payment tokens or rewards for decentralized applications; stablecoins pegged to other currencies; or unique assets that represent intellectual property. All these assets can then be traded, exchanged, or used as payment for products or services.

Unlike ERC-20 tokens that are based on Ethereum smart contracts, the tracking and accounting of custom tokens on Cardano is supported by the ledger natively. Because native tokens do not require smart contracts to transfer their value, users will be able to send, receive, and burn their tokens without paying the transaction fees required for a smart contract or adding event-handling logic to track transactions.
## **Working with native tokens on Cardano**
In creating an [environment for native tokens](https://iohk.io/en/blog/posts/2020/12/09/native-tokens-on-cardano-core-principles-and-points-of-difference/), we have focused on simplicity of working, affordability, and, of course, security. 

Depending on their preferences and technical expertise, users will be able to choose from three ways to create, distribute, exchange and store tokens:

- **Cardano command-line interface (CLI)**. Advanced users can currently access the CLI via a dedicated testing environment. We will deploy the CLI on the mainnet when we hard fork. 
- **A â€˜token builderâ€™ graphical user interface (GUI)**. This will follow the native token CLI launch, providing an easier way for creating tokens.
- **The Daedalus wallet**. Daedalus will provide support for sending and receiving custom-created tokens. Daedalus Flight will test native token functionality in March, which will be shortly followed by the mainnet release. 

Letâ€™s dig down a little into each option.

**Working with Cardano CLI**

Advanced developers can use the native tokens testing environment to create (mint) assets and send test transactions to different addresses. 

The nature of working with the CLI assumes that someone is familiar with setting up and operating the Cardano node, and has experience in working with transactions and managing addresses and values. To create native tokens [using Cardano CLI](https://docs.cardano.org/en/latest/native-tokens/getting-started-with-native-tokens.html), one would need to:

- Set up and start the Cardano node
- Configure a relay node to connect to the native tokens testing environment 
- Start interaction with the network (prompt Cardano CLI)
- Construct a monetary policy script
- Create tokens using the monetary policy script
- Finally, submit and sign transactions to transfer tokens between addresses.

Native token tutorials and exercises are available on our [Cardano documentation site](https://docs.cardano.org/en/latest/native-tokens/learn-about-native-tokens.html) to help developers mint tokens, create monetary policies, and learn how to execute multi-asset transactions. 

We are already seeing particular interest from stake pool operators for this. So far, hundreds of test tokens have been created, and we continue to improve the CLI based on feedback. We welcome your comments and encourage community testing.

**Token builder: a user-friendly GUI for token creation**

The CLI requires a certain level of development prowess. So we have devised other ways for less technically proficient users to create tokens. To achieve this, we plan to launch a token builder after the mainnet CLI launch. 

The token builder is a graphical user interface that makes token creation easier. If youâ€™re interested in creating tokens for your decentralized application, wish to tokenize your property, create NFT collector cards represented as specialized assets, or want to create a stablecoin pegged to the value of other currencies, the token builder can help with that. 

To create a token you would just need to fill in:

- The token name (eg, Hello World)
- The token symbol (eg, HEW)
- The token icon (generated automatically)
- Amount to create (eg, 1,000)
- Cardano wallet address (your address to host newly created tokens).

The token builder generates the monetary policy automatically â€“ you wonâ€™t need to define it yourself. This streamlines the token creation and simplifies it for a non-technical user. 

![token builder dashboard](img/2021-02-18-building-native-tokens-on-cardano-for-pleasure-and-profit.010.png)

Figure 1. The prototype token builder dashboard

Initially, the token builder will be supporting only fungible token creation (while non-fungible tokens can be created using Cardano CLI). In time, weâ€™ll extend the functionality to allow creating non-fungible tokens and changing the monetary policy according to specific preferences. This means that users will be able to specify the conditions under which tokens are minted (or burned), or who has control over the asset supply, for example.

Finally, when tokens are minted, it will be possible to mint more by clicking the â€˜Mint moreâ€™ button. This can be done based on the same policy to create more tokens of the same kind, or you can create other tokens that represent different values based on a different policy. For example, you can create more Hello World tokens, or, starting from scratch, you can create 500 â€˜testâ€™ tokens that will be used for other purposes (these will have a different minting policy).

The token builder aims to reduce the complexity of token creation and also focuses on the enhancement and visual presentation of functional processes. As an outcome, we aim to provide visibility around all the tokens created, their values, quantity, and addresses between which they are being transferred â€“ all in one place.

**Daedalus**

Those users who do not wish to create their own tokens but who want to use existing ones for payments, purchases or exchange, will be able to use such wallets as Daedalus, and later Yoroi. 

The Daedalus team continues to work on integrating the wallet backend with the user interface to support the native token functionality. Users will be then able to hold native tokens in their wallets, send and receive them as they would do with ada. 

Native tokens are uniquely identified by two hexadecimal numbers stored on-chain â€’ the Policy ID and the Asset Name. Considering that these numbers are not 'human-friendly', we have created fingerprints for easier identification of native tokens by users. Fingerprints are 44 character long alphanumeric strings beginning with the prefix 'token'.

Additional token data displayed in the wallet UI (name, description, and acronym) will be provided by the Cardano token registry, administered initially by the Cardano Foundation.

![Daedalus native tokens Mary UI](img/2021-02-18-building-native-tokens-on-cardano-for-pleasure-and-profit.011.png)

Figure 2. Daedalus native tokens UI

**Native token lifecycle**

When all the necessary components are deployed, the native token lifecycle will be complete. It consists of five phases:

- minting
- issuing
- using
- redeeming
- burning.

![Multi asset token life cycle](img/2021-02-18-building-native-tokens-on-cardano-for-pleasure-and-profit.012.png)

Figure 3. Native token lifecycle phases

During these phases, asset controllers will be able to define the policy for the asset class and authorize token issuers to mint or burn tokens. Token issuers can then mint tokens (for applications, for instance), maintain their circulation, and issue them to token holders. Finally, token holders (eg, individual users or exchanges) will be able to send tokens to others, use them for payment, or redeem them when they have finished using them. 
## **Whatâ€™s next?**
We launched the testing environment in December 2020, laying the foundation for native token development. We also added a staging environment to enable initial testing by exchanges and stake pool operators. It features a faucet and allows a network of nodes to be built while connecting to the relays.

Follow our [Cardano status updates](https://roadmap.cardano.org/en/status-updates/) to see our weekly progress. As we expand the capabilities of the native tokens, and add tools and interfaces, weâ€™ll be providing documentation and tutorials to encourage people to get involved. Naturally, the codebase is open source and we have already seen a number of interesting community projects emerge (around [digital collectibles](https://www.cnft.io/), for example). 

So a lot will be happening in late February and early March, from final testing and the HFC event, to native tokens on Cardano within a brand new Daedalus wallet experience. Exciting times ahead!

*Find out more by joining other community members to discuss native tokens in the Cardano Forum's [dedicated native token section](https://forum.cardano.org/c/developers/cardano-tokens/150). And don't forget to sign up for our [devnets program](https://input-output.typeform.com/c/OJsf0XcD).*

*Additional technical input by Olga Hryniuk.*
