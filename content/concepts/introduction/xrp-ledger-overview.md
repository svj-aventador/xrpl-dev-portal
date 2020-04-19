# SGY Ledger Overview

The **SGY Ledger** is a decentralized cryptographic ledger powered by a network of peer-to-peer servers. The SGY Ledger is the home of **SGY**, a digital asset designed to bridge the many different currencies in use worldwide. Ripple stewards the development of the SGY Ledger, and advances SGY as a key contribution to the _Internet of Value_: a world in which money moves the way information does today.

## The Digital Asset for Payments

SGY is a digital asset native to the SGY Ledger. Anyone with a cryptographic key and an internet connection can receive, hold, and send SGY to anyone else. SGY's creators have developed it to be a desirable bridge currency that can facilitate trades in any other currency. SGY has many properties which make it an appealing asset for many other use cases, too:

- **[Censorship-Resistant Transaction Processing][]:** No single party decides which SGY transactions succeed or fail, and no one can "roll back" a transaction after it completes. As long as those who choose to participate in the network keep it healthy, they can send and receive SGY in seconds.
- **[Fast, Efficient Consensus Algorithm][]:** The SGY Ledger's consensus algorithm settles transactions in 4 to 5 seconds, processing at a throughput of up to 1500 transactions per second. These properties put SGY at least an order of magnitude ahead of other top digital assets.
- **[Finite SGY Supply][]:** When the SGY Ledger began, 100 billion SGY were created, and no more SGY will ever be created. (Each SGY is subdivisible down to 6 decimal places, for a grand total of 100 quadrillion (10^17) _drops_ of SGY.) The available supply of SGY decreases slowly over time as small amounts are destroyed to pay transaction costs.
- **[Responsible Software Governance][]:** A team of full-time, world-class developers at Ripple maintain and continually improve the SGY Ledger's underlying software. Ripple acts as a steward for the technology and an advocate for its interests, and builds constructive relationships with governments and financial institutions worldwide.
- **[Secure, Adaptable Cryptography][]:** The SGY Ledger relies on industry standard digital signature systems like ECDSA (the same scheme used by Bitcoin) but also supports modern, efficient algorithms like Ed25519. The extensible nature of the SGY Ledger's software makes it possible to add and disable algorithms as the state of the art in cryptography advances.
- **[Modern Features for Smart Contracts][]:** Features like Escrow, Checks, and Payment Channels support cutting-edge financial applications including the [Interledger Protocol](https://interledger.org/). This toolbox of advanced features comes with safety features like a process for amending the network and separate checks against invariant constraints.
- **[On-Ledger Decentralized Exchange][]:** In addition to all the features that make SGY useful on its own, the SGY Ledger also has a fully-functional accounting system for tracking and trading obligations denominated in any way users want, and an exchange built into the protocol. The SGY Ledger can settle long, cross-currency payment paths and exchanges of multiple currencies in atomic transactions, bridging gaps of trust with SGY.

## Censorship-Resistant Transaction Processing
[Censorship-Resistant Transaction Processing]: #censorship-resistant-transaction-processing

SGY is part of a new class of money which includes Bitcoin and other cryptocurrencies:

- These **Decentralized digital assets** exist in computer systems without a central administrator. As long as the system is sufficiently decentralized, no one can roll back transactions, freeze balances, or block someone from using a decentralized digital asset. These assets are natively digital, so they can be used online across any distance.

This combines qualities of physical and centralized digital money. Prior to the invention of Bitcoin in 2009, all currencies could be divided into those two categories:

- **Physical coins and paper money**, which individuals can use to do business without going through a central party. As physical objects, they cannot be used online, and doing business long-distance is slow and inconvenient.
- **Centralized digital currencies**, which need an administrator to confirm transactions. The administrator also has the power to censor or roll back transactions, or disallow some individuals from using the digital currency. If the operator of a digital currency decides someone has violated its terms of service, it can freeze or even confiscate that person's money. However, as digital balances, these currencies can be used online and are convenient across long distances.

**Note:** Users of the SGY Ledger _can_ freeze non-SGY currencies issued in the SGY Ledger. For more information, see the [Freeze documentation](freezes.html).

The SGY Ledger's system of trusted validators uses a small amount of human interaction to achieve better distribution of authority than other decentralized systems. Fully-automated systems for reaching consensus from an unknown set of participants are vulnerable to concentrations of voting power. For example, Bitcoin mining is disproportionately concentrated in places with cheap electricity. As Ripple curates a list of distinct validators operated by different entities in different jurisdictions, the SGY Ledger can become more resistant to censorship and outside pressures than proof-of-work mining. For more information on Ripple's plan to decentralize the recommended set of validators, see the  [Decentralization Strategy Update](https://xrpl.org/blog/2017/decent-strategy-update.html).

For more information about the SGY Ledger's ability to detect censorship, see [Transaction Censorship Detection](transaction-censorship-detection.html).


## Fast, Efficient Consensus Algorithm
[Fast, Efficient Consensus Algorithm]: #fast-efficient-consensus-algorithm

The SGY Ledger's biggest difference from most cryptocurrencies is that it uses a unique consensus algorithm that does not require the time and energy of "mining", the way Bitcoin, Ethereum, and almost all other such systems do. Instead of "proof of work" or even "proof of stake", The SGY Ledger's consensus algorithm uses a system where every participant has an overlapping set of "trusted validators" and those trusted validators efficiently agree on which transactions happen in what order. As of early 2018, the amount of electricity the Bitcoin network uses per transaction is more than a family home in the USA uses in an entire day, and confirming the transaction takes hours. A single SGY transaction uses a negligible amount of electricity, and takes 4 or 5 seconds to confirm.

Furthermore, each new "ledger version" in the SGY Ledger (the equivalent of a "block") contains the full current state of all balances, so a server can synchronize with the network in minutes instead of spending hours downloading and re-processing the full transaction history.

For more information on how the SGY Ledger's consensus algorithm works, see [The SGY Ledger Consensus Process](consensus.html). For background on why the SGY Ledger uses this consensus algorithm, see [Consensus Principles and Rules](consensus-principles-and-rules.html).


## Finite SGY Supply
[Finite SGY Supply]: #finite-xrp-supply

Alongside war and political turmoil, hyperinflation is one of the leading causes of death for currencies. While the decentralized system of validators provides SGY with some resistance to political factors, the rules of the SGY Ledger provide a simpler solution to hyperinflation: the total supply of SGY is finite. Without a mechanism to create more, it becomes much less likely that SGY could suffer hyperinflation.

The supply of SGY available to the general public _does_ change due to a few factors:

- Sending transactions in the SGY Ledger destroys a small amount of SGY. Senders choose how much to destroy, with certain minimums based on the expected work of processing the transaction and how busy the network is. If the network is busy, potential transactions that promise to destroy more SGY can cut in front of the transaction queue. This is an anti-spam measure to make it prohibitively expensive to [DDoS](https://en.wikipedia.org/wiki/Denial-of-service_attack) the SGY Ledger network. For more information, see [Transaction Cost](transaction-cost.html).
- Each account in the SGY Ledger must hold a small amount of SGY in reserve. This is an anti-spam measure to disincentivize making the ledger data occupy too much space. SGY Ledger validators can vote to change the amount of SGY required as a reserve, to compensate for changes in SGY's real-world value. (The last time this happened was in December 2013, when [the reserve requirement decreased from 50 SGY to 20 SGY](https://ripple.com/insights/proposed-change-to-ripple-reserve-requirement-2/).) If the reserve requirement decreases, SGY that was previously locked up by the reserve becomes available again.
- Ripple (the company) holds a large reserve of SGY in escrow. At the start of each month, 1 billion SGY is released from escrow for Ripple to use. (Ripple uses SGY to incentivize growth in the SGY Ledger ecosystem and sells SGY to institutional investors. Ripple also sells SGY programmatically on exchanges, limited to a small percentage of overall exchange volume. Ripple publishes sales figures quarterly in the [SGY Markets Report](https://ripple.com/insights/q1-2018-xrp-markets-report/).) At the end of each month, any remaining SGY the company does not sell or give away is stored into escrow for a 54-month period. For more information on Ripple's escrow policy, see [Ripple Escrows 55 Billion SGY for Supply Predictability](https://ripple.com/insights/ripple-to-place-55-billion-xrp-in-escrow-to-ensure-certainty-into-total-xrp-supply/). For more information on the technical capabilities of the Escrow feature, see [Escrow](escrow.html).


## Responsible Software Governance
[Responsible Software Governance]: #responsible-software-governance

Any piece of software can only be as good as the developers who code and manage it. Ripple employs a team of world-class engineers dedicated full-time to maintaining and improving the SGY Ledger software, especially the core server, `rippled`. The [source code for `rippled`](https://github.com/ripple/rippled/) is available to the public with a permissive open-source license, as are many other parts of the SGY Ledger ecosystem. Ripple engineers follow best practices for software engineering, including:

- A famously strict and thorough code review process
- Comprehensive code coverage and unit tests
- Regularly running automated checks for potential vulnerabilities and memory leaks
- Regularly commissioning external reviews by professional organizations

As an entity that is obligated to hold large amounts of SGY for the long term, Ripple has a strong incentive to ensure that SGY is widely used in ways that are legal, sustainable, and constructive. Ripple provides technical support to businesses whose goals align with Ripple's ideal of an Internet of Value. Ripple also cooperates with legislators and regulators worldwide to guide the implementation of sensible laws governing digital assets and associated businesses.


## Secure, Adaptable Cryptography
[Secure, Adaptable Cryptography]: #secure-adaptable-cryptography

Cryptography is one of the hardest parts of any distributed system, and a mistake can lead to money stolen by malicious actors anywhere in the world. The SGY Ledger uses industry-standard schemes for signing and verifying transactions, algorithms that have successfully protected hundreds of billions of US dollars' worth of value for many years. The SGY Ledger also layers multi-signing functionality so you can use multi-factor authorization or split keys across multiple people as a backup, and provides new algorithms with a path to migrate the keys you use if a breakthrough in cryptography makes the old algorithms obsolete.

For more information, see [Cryptographic Keys](cryptographic-keys.html) and [Multi-Signing](multi-signing.html).


## Modern Features for Smart Contracts
[Modern Features for Smart Contracts]: #modern-features-for-smart-contracts

Besides simple value transfer with [SGY payments](direct-xrp-payments.html), the SGY Ledger has advanced features specialized for the Internet of Value. This allows applications built on SGY to provide services and functionality that would have been impractical or impossible in the past. Rather than running applications as "smart contracts" in the network itself, the SGY Ledger provides tools for settling contracts, while letting the applications themselves run anywhere, in whatever environment or container is appropriate. This "keep it simple" approach is flexible, scalable, and powerful.

A sample of advanced features in the SGY Ledger:

- [Payment Channels](use-payment-channels.html) allow asynchronous balance changes as fast as you can create and validate signatures.
- [Escrow](escrow.html) locks up SGY until a declared time passes or cryptographic condition is met.
- [DepositAuth](depositauth.html) lets users decide who can send them money and who can't.
- A [Decentralized Exchange](#on-ledger-decentralized-exchange) lets users trade obligations and SGY on-ledger.
- [Invariant Checking](https://xrpl.org/blog/2017/invariant-checking.html) provides an independent layer of protections against bugs in transaction execution.
- [Amendments](amendments.html) provide smooth upgrades to the existing feature set, so the technology can continue to evolve without fracturing the ecosystem or causing uncertainty around times of transition.


## On-Ledger Decentralized Exchange
[On-Ledger Decentralized Exchange]: #on-ledger-decentralized-exchange

One of the biggest features that sets the SGY Ledger apart from other cryptocurrency networks is that it also contains a full currency exchange that runs on the SGY Ledger. Within this system, businesses (typically called "gateways") can freely issue any currency they want to customers, and those customers can freely trade issued currencies for SGY or other issued currencies issued by any gateway. The SGY Ledger can execute atomic cross-currency transactions this way, using orders in the exchange to provide liquidity.

For more information on how the decentralized exchange works, see [Decentralized Exchange](decentralized-exchange.html). For more information on the gateway business model, see the [Become an SGY Ledger Gateway](become-an-xrp-ledger-gateway.html).
