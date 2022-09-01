# Ensuring ETC Network Security
### **Ensuring ETC network security - a comparison of 51% Attack Resistance proposals for Ethereum Classic**
![](img/2020-10-23-ensuring-etc-network-security.002.png) 23 October 2020![](img/2020-10-23-ensuring-etc-network-security.002.png)[ Brian McKenna](tmp//en/blog/authors/brian-mckenna/page-1/)![](img/2020-10-23-ensuring-etc-network-security.003.png) 4 mins read

![Brian McKenna](img/2020-10-23-ensuring-etc-network-security.004.png)[](tmp//en/blog/authors/brian-mckenna/page-1/)
### [**Brian McKenna**](tmp//en/blog/authors/brian-mckenna/page-1/)
Product Manager

Operations

- ![](img/2020-10-23-ensuring-etc-network-security.005.png)[](https://www.linkedin.com/in/brian-mckenna-a284341a/ "LinkedIn")
- ![](img/2020-10-23-ensuring-etc-network-security.006.png)[](https://twitter.com/BrianMc36431138 "Twitter")
- ![](img/2020-10-23-ensuring-etc-network-security.007.png)[](https://github.com/brian-mckenna "GitHub")

![Ensuring ETC Network Security](img/2020-10-23-ensuring-etc-network-security.008.jpeg)

The Ethereum Classic network suffered from four 51% attacks between 2019 and 2020. Three of those attacks have occurred recently â€“ with just weeks between each other â€“ which resulted in expensive losses for stakeholders due to double spending and service disruption. A number of Ethereum Classic Improvement Proposals (ECIPs) followed after these attacks aiming to provide the immediate solution for 51% attack resistance.

IOHK, andÂ [ETC Coop](https://etccooperative.org/)Â have collaborated to provide Ethereum Classic stakeholders and the broader community with the knowledge and understanding on how to resist these issues. To support this activity, we have created aÂ [comparison document](https://static.iohk.io/docs/etc/ecip-comparison-for-51-attack-resistance.pdf)Â to showcase and summarize the different 51% attack mitigations. In it, ETC community members will be able to assess each proposal, understand any concerns, and be advised on how the ETC community can solve ETC network security issues together.

The ECIP that seems to be reaching adoption in the immediate term is ECIP 1100: Modified Exponential Subjective Scoring ([MESS](https://ecips.ethereumclassic.org/ECIPs/ecip-1100)). MESS is a modified version of Vitalik Buterinâ€™s Exponential Subjective Scoring (ESS) and aims to make larger chain reorganizations more difficult. However, we believe that it will not provide robust security and there is no guarantee that it will prevent further attacks. Whatâ€™s most concerning, however, about MESS, is that it has not been formally studied nor has its security been proven. Moreover, a series of potential attack vectors on MESS have already been identified.
## **Checkpointing is the way forward**
[Checkpointing](https://ecips.ethereumclassic.org/ECIPs/ecip-1097), on the other hand, can make 51% attacks impossible with deterministic confidence of finality. This approach grants the ETC core developer community a safe space to innovate and implement the more speculative proposals that are underway. These may include MESS, Reducing the dag, Keccak-256, and many others. Considering that ETC value and user experience is currently hindered by the low-confidence and subjective finality of MESS, MESS doesnâ€™t provide high confidence for stakeholders to reduce confirmation times to desirable levels.

The Ethereum Classic network is a minority proof of work blockchain in the Ethash environment. As of October 08, 2020, the Ethereumâ€™s network hashrate is ~248.16 TH/s, Nicehashâ€™s hashrate is ~9.34 TH/s, while Ethereum Classicâ€™s network hashrate is only ~3.47 TH/s . This means that Ethereum Classicâ€™s hashrate is only ~1.5% of Ethereumâ€™s and ~40% of Nicehashâ€™s, which is just one of many other mining rental platforms. It should be noted though, that non-Ethash networks that are minable by general purpose hardware can also be turned on to Ethereum Classic, which means that the Ethereum Classic network is even more of a minority proof of work blockchain than represented by the Ethereum and Nicehash comparisons above.

It thus follows that the current security assumptions of the Ethereum Classic network no longer hold. Speculating ETCâ€™s network security on ETHâ€™s proof of stake timeline is also not a sustainable security strategy and arguably not competitive enough to increase the value of the network.
## **Looking to the future**
Indeed, it goes further than that. ETC is at an important crossroads and the choices we make now will impact not only the future of the platform but of the whole ecosystem. Any 51% attack mitigation must be robust enough to give absolute certainty to ETC holders, users and service providers that their transactions will be secure.

We need to be decisive and resolute, while giving ourselves the time to get this right. If we adopt a suboptimal solution at this point, and there are further issues with the network, it is unlikely that our (thus far) patient stakeholders â€“ especially exchanges â€“ will remain so.

Our focus at the moment is rightly on mitigation. But letâ€™s also ensure we remember the longer-term goal â€“ the health and sustainable success of Ethereum Classic. Letâ€™s move decisively to underpin the security of the network, and together look forward towards a new era of network growth, community growth and sustainable innovation.

*This post was originally published on the [ETC Cooperative blog*](https://etccooperative.org/posts/2020-10-20-ensuring-etc-network-security)*
