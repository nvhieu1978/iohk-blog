# Cardano’s Extended UTXO accounting model – built to support multi-assets and smart contracts
### **Cardano uses an innovative Extended UTXO accounting model to support multi-assets and smart contracts. In the first of a two-part blog, we look at the different blockchain accounting systems and why EUTXO matters**
![](img/2021-03-11-cardanos-extended-utxo-accounting-model.002.png) 11 March 2021![](img/2021-03-11-cardanos-extended-utxo-accounting-model.002.png)[ Fernando Sanchez](tmp//en/blog/authors/fernando-sanchez/page-1/)![](img/2021-03-11-cardanos-extended-utxo-accounting-model.003.png) 5 mins read

![Fernando Sanchez](img/2021-03-11-cardanos-extended-utxo-accounting-model.004.png)[](tmp//en/blog/authors/fernando-sanchez/page-1/)
### [**Fernando Sanchez**](tmp//en/blog/authors/fernando-sanchez/page-1/)
Technical Writer

Marketing and Communications

- ![](img/2021-03-11-cardanos-extended-utxo-accounting-model.005.png)[](mailto:fernando.sanchez@iohk.io "Email")
- ![](img/2021-03-11-cardanos-extended-utxo-accounting-model.006.png)[](https://www.linkedin.com/in/linkedinsanchezf/ "LinkedIn")

![Cardano’s Extended UTXO accounting model – built to support multi-assets and smart contracts](img/2021-03-11-cardanos-extended-utxo-accounting-model.007.jpeg)

Blockchain networks are complex data structures. Transactions continuously crisscross the chain, creating digital footprints that require careful tracking and management to maintain the integrity and reliability of the underlying ledger.

Two major accounting ledgers exist in the blockchain space: UTXO-based blockchains (Bitcoin, for instance), and Account/Balance chains (Ethereum, and others).

Each of these crypto heavyweights differs in many fundamental ways, but this article focuses on their accounting models. Bitcoin uses an Unspent Transaction Output (UTXO) model, whereas Ethereum deploys an Account/Balance one.

Cardano sought to combine Bitcoin’s UTXO model with Ethereum’s ability to handle smart contracts into an Extended UTXO (EUTXO) accounting model. The adoption of EUTXO facilitates the implementation of smart contracts into the Cardano chain.
### **What is a blockchain accounting model?**
Every company, firm, or commercial entity requires a balance sheet to keep an accurate record of profit, loss, cash flow, and other parameters. By maintaining careful accounting of all this data, companies can, at a glance, visualize their financial status at any given point in time. A company's accounting ledger offers another advantage: The ability to trace the provenance and ownership of funds.

Blockchain networks also require an accounting model to determine who owns what coins (and how many of them), track where those coins go, which ones are used up, and which ones remain available to be spent.
### **UTXO model v Account/Balance model: A brief overview**
Decades ago, accountants used physical ledger books with handwritten entries to keep records about the movement of funds. Nowadays, companies use electronic versions of the same thing. Blockchains use transactions as records (much like entries on a ledger book) to track provenance and ownership. These transactions contain a lot of information (where the coins come from, where they're going, and whatever change is leftover from these transactions). 

Here’s a brief overview of the UTXO and Account/Balance models:
### **UTXO**
In a UTXO model, the movement of assets is recorded in the form of a directed acyclic graph where the nodes are transactions and the edges are transaction outputs, where each additional transaction consumes some of the UTXOs and adds new ones. The users' wallets keep track of a list of unspent outputs associated with all addresses owned by the user, and calculate the users’ balance.

UTXO is, in many ways, similar to cash. A good analogy is this: Imagine you have $50 in your wallet. This amount could be made up with several combinations: two $20 bills and one $10, four $10 bills and two $5 bills, and many others. But regardless of the permutations, the amount ($50) remains equal. UTXOs work in the same way. Whatever balance you have in your blockchain wallet (say, 150 coins) could be made up with many different UTXO combinations, based on previous transactions, but the balance amount remains the same. In other words, the balance held in a given wallet address is the sum of all unspent UTXOs from previous transactions.
### **The concept of 'change' in UTXO models**
Much like cash transactions in any store, UTXOs introduce ‘change.’ When you take out say a $50 bill from your wallet, you cannot tear that bill into smaller pieces to pay for something that costs $15, for example. You have to hand over the entire $50 bill and receive your change from the cashier. UTXOs work in the same way. You cannot ‘split’ a UTXO into smaller bits. UTXOs are used whole, and change given back to your wallet’s address in the form of a smaller UTXO.
### **The advantages of UTXO models**
By checking and tracking the size, age, and amount of UTXOs being transferred around, one can extract accurate metrics about the blockchain’s usage and financial activity of the chain.

UTXO models offer other advantages. Better scalability and privacy, for example. Also, the transaction logic is simplified, as each UTXO can only be consumed once and as a whole, which makes transaction verification much simpler.

To sum UTXO up:

- A UTXO is the output of a previous transaction, which can be spent in the future
- UTXO chains have no accounts. Instead, coins are stored as a list of UTXOs, and transactions are created by consuming existing UTXOs and producing new ones in their place
- Balance is the sum of UTXOs controlled by a given address
- UTXOs resemble cash in that they use ‘change’, and are indivisible (UTXOs are used whole)
### **The Account/Balance model**
As the name indicates, blockchain models that deploy an Account/Balance accounting model use an account (which can be controlled by a private key or a smart contract) to hold a coin balance. In this model, assets are represented as balances within users’ accounts, and the balances are stored as a global state of accounts, kept by each node, and updated with every transaction.

In many respects, Account/Balance chains (such as Ethereum) operate in a similar fashion to traditional bank accounts. The wallet's balance increases when coins are deposited, and decreases when coins are transferred elsewhere. The crucial difference here is that, unlike UTXOs, you can use your balance partially. So for example, if you have 100 ETH in your account, you can send a portion of that (say, 30 ETH) to someone else. The resulting balance will be 70 ETH remaining in your account, and the address where you sent the coins to will increase by 30 ETH. The concept of change does not apply in Account/Balance accounting models as it does in UTXO ones.

To sum up the Account/Balance model:

- This accounting model resembles how a bank operates
- Users have accounts that hold their coin balance
- It is possible to spent partial balances
- The concept of change does not apply

Tomorrow, in the second part of this analysis, we'll discuss how each model deals with transactions, explain the rationale for developing the EUTXO model for Cardano, and provide an in-depth explanation of what EUTXO is and how it works.
