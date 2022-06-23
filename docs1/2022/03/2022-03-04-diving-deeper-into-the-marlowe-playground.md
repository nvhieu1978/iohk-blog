# Diving deeper into the Marlowe Playground
### **Learn how to make your own templates from Marlowe contracts and provide hints to users using custom metadata**
![](img/2022-03-04-diving-deeper-into-the-marlowe-playground.002.png) 4 March 2022![](img/2022-03-04-diving-deeper-into-the-marlowe-playground.002.png)[ Pablo Lamela](tmp//en/blog/authors/pablo-lamela-seijas/page-1/)![](img/2022-03-04-diving-deeper-into-the-marlowe-playground.003.png) 7 mins read

![Pablo Lamela](img/2022-03-04-diving-deeper-into-the-marlowe-playground.004.png)[](tmp//en/blog/authors/pablo-lamela-seijas/page-1/)
### [**Pablo Lamela**](tmp//en/blog/authors/pablo-lamela-seijas/page-1/)
Research Fellow

Research

- ![](img/2022-03-04-diving-deeper-into-the-marlowe-playground.005.png)[](mailto:pablo.lameja-seijas@iohk.io "Email")
- ![](img/2022-03-04-diving-deeper-into-the-marlowe-playground.006.png)[](https://www.linkedin.com/in/palas87/ "LinkedIn")
- ![](img/2022-03-04-diving-deeper-into-the-marlowe-playground.007.png)[](https://github.com/palas "GitHub")

![Diving deeper into the Marlowe Playground](img/2022-03-04-diving-deeper-into-the-marlowe-playground.008.jpeg)

Marlowe is a domain-specific language (DSL) embedded in Haskell that offers financial contracts for blockchain that everyone can code. It is a platform for decentralized finance (DeFi) that supports direct, peer-to-peer lending, contracts for difference (CFD), and other similar instruments. Marlowe allows users to apply their domain expertise to write and manage contracts conveniently, without the steep learning curve associated with software development, blockchain, or smart contracts.

The [Marlowe Playground](https://play.marlowe-finance.io/#/) is the sandbox environment where you can practice writing your financial contracts. This playground offers you a choice of working directly in a range of languages such as Marlowe itself, [JavaScript](https://play.marlowe-finance.io/doc/marlowe/tutorials/javascript-embedding.html), [Haskell](https://play.marlowe-finance.io/doc/marlowe/tutorials/embedded-marlowe.html), or [Blockly](https://play.marlowe-finance.io/doc/marlowe/tutorials/playground-blockly.html), depending on which you prefer to use. We have recently added new features to the Marlowe Playground for constructing and editing templates and customizing metadata, as well as a new JSON download option for the contracts themselves. In this post, we take a closer look at these new features.
### **From contracts to templates**
With the introduction of Marlowe Run, we have extended the Marlowe Playground to support what we call *templates*. These *templates* are implemented using an extended version of Marlowe (known as Extended Marlowe, the version available in the Marlowe Playground). These new templates will mean users can easily reuse and repurpose contracts for different scenarios and contexts. 

Extended Marlowe offers greater flexibility than plain Marlowe (or Core Marlowe). Contracts are very concrete, and specify timeouts in absolute values, originally through slot numbers, and more recently using standardized timestamps (POSIX time).

Additionally, Marlowe Values are typically hardcoded in Marlowe, except those passed as Inputs. For example, you can implement a loan for â‚³100 or one that asks the user how much to lend through a Choice in a When construct, but we could not have a reusable Marlowe contract that could be deployed at any time and with any given parameters. Extended Marlowe addresses these limitations by adding the option to include contract parameters. Currently, extended Marlowe is practically identical to plain Marlowe except in that it includes two extra constructors that represent *parameters* of the *template*:

- SlotParam â€” can be written in place of a timeout in a When construct
- ConstantParam â€” is a type of Value construct

Both constructors take, as their only parameter, a string that serves as an identifier for the parameter, for example:

- SlotParam "Payment deadline
- ConstantParam "Price"

Two parameters of the same type (either SlotParam or ConstantParam) and with the same identifier are considered the same parameter, even if they appear in different places.

If a contract contains parameters (in other words, if it is a *template*), then the user will be asked to input values for those parameters before starting a simulation of the contract, or before deploying the contract in Marlowe Run:

![](img/2022-03-04-diving-deeper-into-the-marlowe-playground.009.png)

Figure 1. Simulation dialog

Note that the value template parameter input in the picture is not just an integer input field. Rather, it expects a number with decimals, and it has a label with a currency symbol that indicates that the number expected represents an amount of ada. This rule is also true for values required through a Choice in a When construct. Also, choices do not need to represent amounts of ada. They can represent anything, like a ratio, as follows:

![](img/2022-03-04-diving-deeper-into-the-marlowe-playground.010.png)

Figure 2. Actions dialog

There are also hints for each parameter that a user can display by clicking the purple question mark beside each term. Text in the hints is specific to the contract template, and it contains formatted text, for example, **bold text**, *text in italics*, or underlined text.

![](img/2022-03-04-diving-deeper-into-the-marlowe-playground.011.png)

Figure 3. Parameter hints

User-defined contracts can customize all these details through the use of *metadata*. Letâ€™s take a look at how this is done.
## **Customizing metadata**
There is a *Metadata* tab at the bottom of each of the editors in the Marlowe Playground. There, users can customize the metadata as needed. For example: 

![](img/2022-03-04-diving-deeper-into-the-marlowe-playground.012.png)

Figure 4. Metadata tab

There is some basic metadata that every contract is expected to include, such as:

- **Contract type** â€” What type of contract is it? This category will help classify contracts so that they are easier to find in the future. Currently, there are very few categories available, but we will add more in the future. If no category fits your contract, you can always choose â€œOtherâ€.
- **Contract name** â€” Just a short name to identify the contract.
- **Contract short description** â€” A very brief description to show in listings.
- **Contract long description** â€” A more detailed description that will be shown following the short description in cases when the user has already selected the template and wants to know more (for example, when creating a contract in Marlowe Run).

Note that the text in descriptions supports using some of the formatting functionality included in Markdown. For example, adding two asterisks before and after a part of the text of a description will make that text appear in bold when simulating the contract, as we saw in the previous section. In this way the plain text:

Amount of \*\*money\*\* to pay

will be rendered as

Amount of **money** to pay

We recommend using this functionality to highlight which keywords represent entities that have special meaning in the context of the contract, like names of roles or choices, for example.

The metadata tab also supports specifying hints for the roles, choices, slot, and value parameters defined in the contract, as well as formatting for choices and value parameters.

A new role or choice, slot, or value parameter added to a contract will appear in the Metadata tab in red. In the case of the Haskell and JavaScript editors, it may be necessary to compile the code successfully before this happens.

![](img/2022-03-04-diving-deeper-into-the-marlowe-playground.013.png)

Figure 5. Metadata tab - adding metadata entries

Pressing the red â€œ+â€ button will create a new metadata entry for the given item. In the same way, if a role, choice, or slot or value parameter stops being used in the contract, the existing metadata will be flagged in red for deletion, and the user must press the â€œ-â€ button to delete the metadata entry from the contract.

![](img/2022-03-04-diving-deeper-into-the-marlowe-playground.014.png)

Figure 6. Metadata tab - deleting metadata entries

In addition to the description, in the cases of choices and value parameters, a user can optionally specify a formatting for the number that they want the end user to provide. To do that, select â€œFixed point amountâ€ from the dropdown menu. This will provide two extra fields:

- **Number of decimal digits for value** (bottom left) â€” numbers in Marlowe are internally always integers, but for convenience, users can input numbers as fixed-point. For example, Marlowe amounts of ada are represented in lovelace (a millionth of an ada) but, in general, end users prefer to work with amounts of ada (since they are more readable). Developers can support this by writing 6 in the number of decimal places. As a result, the end user will see a decimal separator in the 6th position, even though internally the contract still works with lovelace (ada units).
- **Currency label for the value** (bottom right) â€” developers can also present a currency symbol near the input box of the value as a hint to end users about the unit of the amount that we expect from them. For example, in the case of ada, just write the ada symbol â€œâ‚³â€.

![](img/2022-03-04-diving-deeper-into-the-marlowe-playground.015.png)

Figure 7. Number formatting

Finally, the order of parameters is important. For example, imagine several slot parameters for the end user to choose. It would be logical to display those parameters in chronological order.

To arrange the metadata, drag entries into the desired order, for example:

![](img/2022-03-04-diving-deeper-into-the-marlowe-playground.016.png)

Figure 8. Metadata ordering

The order of the parameters in the metadata will be used for generating the form shown at the beginning of the simulation or execution of the contract.
# **Conclusion**
With the new template and metadata extensions to Marlowe, contract developers can now provide hints and parameters to make it easier for end users to reuse the same contract in several circumstances, without having to understand the full implementation and the details of the contract.

These are just some of the new improvements that the Marlowe team continues to work on, and we look forward to sharing the details of more enhancements soon.

*To find out more about upcoming Marlowe releases and new features, keep an eye on our social media channels or the new [Marlowe Discord channel](https://discord.com/channels/826816523368005654/936295815926927390/936316494042779698) for more information. Also, stay tuned for details about our first Marlowe Pioneers Program launching soon!*
