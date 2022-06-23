# Cardano's secure switch to decentralization
### **The event will be ushered in with a ‘public assertion of randomness’, featuring entropy infused by the community**
![](img/2021-03-29-the-secure-transition-to-decentralization.002.png) 29 March 2021![](img/2021-03-29-the-secure-transition-to-decentralization.002.png)[ Prof Alexander Russell](tmp//en/blog/authors/alexander-russell/page-1/)![](img/2021-03-29-the-secure-transition-to-decentralization.003.png) 6 mins read

![Prof Alexander Russell](img/2021-03-29-the-secure-transition-to-decentralization.004.png)[](tmp//en/blog/authors/alexander-russell/page-1/)
### [**Prof Alexander Russell**](tmp//en/blog/authors/alexander-russell/page-1/)
Senior Research Fellow

Academic Research

- ![](img/2021-03-29-the-secure-transition-to-decentralization.005.png)[](mailto:alexander.russell@iohk.io "Email")
- ![](img/2021-03-29-the-secure-transition-to-decentralization.006.png)[](tmp///www.youtube.com/watch?v=KkcAic12dvc "YouTube")
- ![](img/2021-03-29-the-secure-transition-to-decentralization.007.png)[](https://github.com/russella "GitHub")

![Cardano's secure switch to decentralization](img/2021-03-29-the-secure-transition-to-decentralization.008.jpeg)

The security of proof-of-stake blockchains is provided by a mutually dependent relationship between its native token and the consensus mechanism that powers it: after all, electing nodes to issue blocks according to their stake requires a consistent global view of the stake distribution, while maintaining consistency itself requires a fair election mechanism. Indeed, the name Ouroboros – a classical symbol suggestive of mathematical recursion – was originally selected to draw attention to this relationship.

The Ouroboros protocol determines block producers via an evolving sequence of leadership nonces – each nonce runs the show for a 120-hour ‘epoch’, during which it contributes to determining which stake pools are chosen as the one-off leaders for block creation. Along with committing new transactions to the ledger, the blocks appearing in each epoch are additionally responsible for generating the leadership nonce for the following epoch – more recursion! All told, the leadership nonces and stake distributions evolve in concert to provide the fundamental ledger properties we demand of the system. 

The Cardano blockchain transitions to fully decentralized block production on March 31. Just afterwards, the running leadership nonce will be enhanced by adding in a ‘transition nonce’ that reflects entropy from a variety of external, unpredictable sources. Specifically, all transactions posted to the blockchain before Wednesday, April 7 at 15:44:51 UTC (slot 151200 of epoch 258) will play a distinguished role in the future of the blockchain: their accumulated hash value, reflected in the ‘previous-block hash’ from the first block on chain created on or after this time, will determine the transition nonce and hence directly contribute to the protocol’s perpetual cycle of randomness generation. 

IO Global scientists and engineers will contribute a number of specific, external, unpredictable sources of entropy. Additionally, to reflect the decentralized nature of Cardano we are asking the extended community, including stake pool operators and developers, to join us (on chain) for an event we’re calling the Cardano public assertion of randomness. This community exercise will establish the once-in-the-system’s-lifetime random 256-bit transition nonce that will herald the protocol’s official transition to decentralized operation.

We’re going to get more technical now so buckle up, or skip to the end.
## **Some background** 
The Ouroboros protocol is organized into five-day (120-hour) periods called ‘epochs’. As described above, these coordinate two critical activities: updating the stake distribution and updating the leadership nonce. The proof of correctness of the protocol shows that it achieves an auspicious steady state: so long as an epoch begins with an unpredictable leadership nonce, it will deliver a fresh, unpredictable leadership nonce to the following epoch. To bootstrap the recursion, this public assertion event is designed to ensure this property of unpredictability. We remark that proof of work protocols are subject to similar randomness demands: famously, Nakamoto included the presumably unpredictable string ‘The Times 03/Jan/2009 Chancellor on brink of second bailout for banks’ in the [genesis block](https://en.bitcoin.it/wiki/Genesis_block#:~:text=Timestamp,days%20after%20the%20genesis%20block.) of Bitcoin.
## **The entropy mechanism and the timeline** 
Cardano’s implementation of the Ouroboros protocol provides an ‘entropy addition mechanism’ that can add a bitstring identified on the blockchain to subsequent leadership nonces; these are exactly the intended targets of the transition nonce. Naturally, this mechanism requires public declaration of the bitstring and explicit, cryptographically secure approval: specifically, only a collection of digitally signed votes from genesis delegates can complete the process. Furthermore, the process has a specific time horizon: votes must appear prior to the 48-hour mark in the epoch.

The epoch beginning on Monday, April 5 at 21:44:51 UTC (epoch 258) will invoke the entropy addition mechanism: in particular, the previous block hash appearing in the first block on or after Wednesday April 7 at 15:44:51 UTC (slot 151200 of epoch 258) will determine the transition nonce; this will take place roughly 42 hours after the epoch has begun and thus leave six hours for the genesis delegates to cast their votes. Recalling the hash chain structure of the Ouroboros blockchain, this hash value depends on the entire blockchain up to that point.

Closely examining the correctness proofs of the protocol paints a more precise picture of the essential properties of the transition nonce: it must rely on random values – introduced in our setting via Cardano blockchain transactions – that cannot be predicted accurately when the stake distribution for the April 10 epoch is settled. This places special emphasis on transactions appearing in the blockchain between the 12-hour mark, when the stake distribution is firmly settled, and the 42-hour mark, when the hash value will be lifted.
## **Entropy sources introduced by IO Global**
While the Cardano community is bound to introduce a wide variety of random sources – see below! – IO Global scientists and engineers will inject transactions with metadata determined by several public sources of entropy: hashes of the closing prices of the New York Stock Exchange on April 6, and real-time seismic data from the US Geological Survey, the University of Athens, and the Japan Meteorological Society. Seismic data from these sources will cover the first 36 hours of the epoch. Further details, including the scripts to be used for harvesting the data and the exact sources, appear in this [public github repository](https://github.com/input-output-hk/cardano-entropy).

We’d also like the more technical members of the Cardano community to join in too, by adding their own contribution to the randomness. Here’s what we’d like you to do.

- Select some entertaining sources of randomness: a lottery drawing from your region, a new RSA public key generated using your standard tools, or the outcome of a number of rolls of a 20-sided die. 
- Paste the result of these sources into a text document, save it, and hash the file using your favorite hash function, such as SHA256. Post this hash on the blockchain using a [transaction with metadata](https://github.com/input-output-hk/cardano-node/blob/master/doc/reference/tx-metadata.md). (See [this video](https://www.youtube.com/watch?v=fxNx4W1_gro&list=PLnPTB0CuBOBxjtuyI7sseODnMffpVHS2v&index=3&t=3s).)
- To be most useful, your source of randomness should be determined after Tuesday, April 6 at 9:44:51 UTC (slot 43200 of epoch 258) and must be included in a blockchain transaction before Wednesday, April 7 at 15:44:51 UTC (slot 151200 of epoch 258).

If you are less technical, you can still join in. You might like to test out an interesting new community tool, [Cardano Wall](https://cardanowall.com/en/). This allows you to easily write to the Cardano blockchain. However you choose to get involved, please announce your act of community service on social media, by publishing both your (unhashed) source along with the hash value appearing in your transaction.

*Thanks for your support and we’re looking forward to slot 151200 when we can convene, in spirit, for a ‘block party’ to watch the genesis delegates’ votes appear on-chain!*
