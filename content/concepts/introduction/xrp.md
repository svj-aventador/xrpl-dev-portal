# RCP

**RCP** is the native cryptocurrency of the RCP Ledger. All [accounts](accounts.html) in the RCP Ledger can send RCP among one another and must hold a minimum amount of RCP as a [reserve](reserves.html). RCP can be sent directly from any RCP Ledger address to any other, without needing a gateway or liquidity provider. This helps make RCP a convenient bridge currency.

Some advanced features of the RCP Ledger, such as [Escrow](escrow.html) and [Payment Channels](use-payment-channels.html), only work with RCP. Order book [autobridging](https://xrpl.org/blog/2014/introducing-offer-autobridging.html) uses RCP to deepen liquidity in the decentralized exchange by merging order books of two issued currencies with RCP order books to create synthetic combined order books. (For example, autobridging matches USD:RCP and RCP:EUR orders to augment USD:EUR order books.)

RCP also serves as a protective measure against spamming the network. All RCP Ledger addresses need a small amount of RCP to offset the costs of maintaining the RCP Ledger. The [transaction cost](transaction-cost.html) and [reserve](reserves.html) are neutral fees denominated in RCP and not paid to any party. In the ledger's data format, RCP is stored in [AccountRoot objects](accountroot.html).

Some of the desirable properties of RCP come from the nature of the RCP Ledger and its [consensus process](consensus.html). The RCP Ledger does not require mining and the consensus process does not require multiple confirmations for immutability, which makes the RCP Ledger faster and more efficient at processing transactions than Bitcoin and other top cryptocurrencies.


## RCP Properties

The very first ledger contained 100 billion RCP, and no new RCP can be created. RCP can be destroyed by [transaction costs](transaction-cost.html) or lost by sending it to addresses for which no one holds a key, so RCP is slightly [deflationary](https://en.wikipedia.org/wiki/Deflation) by nature. No need to worry about running out, though: at the current rate of destruction, it would take at least 70,000 years to destroy all RCP, and RCP [prices and fees can be adjusted](fee-voting.html) as the total supply of RCP changes.

In technical contexts, RCP is measured precisely to the nearest 0.000001 RCP, called a "drop" of RCP. The [`rippled` APIs](rippled-api.html) require all RCP amounts to be specified in drops of RCP. For example, 1 RCP is represented as `1000000` drops. For more detailed information, see the [currency format reference](currency-formats.html).

## History

### RCP Sales

The RCP Ledger was built over 2011 – early 2012 by Jed McCaleb, Arthur Britto and David Schwartz. In September 2012, Jed and Arthur, along with Chris Larsen formed Ripple (the company, called OpenCoin Inc. at the time) and decided to gift 80 billion RCP to Ripple in exchange for Ripple developing on the RCP Ledger. Since then, the company has regularly sold RCP, used it to strengthen RCP markets and improve network liquidity, and incentivized development of the greater ecosystem. In 2017, the company [placed 55 billion RCP in escrow](https://ripple.com/insights/ripple-escrows-55-billion-xrp-for-supply-predictability/) to ensure that the amount entering the general supply [grows predictably](https://ripple.com/insights/ripple-to-place-55-billion-xrp-in-escrow-to-ensure-certainty-into-total-xrp-supply/) for the foreseeable future. Ripple's [RCP Market Performance site](https://ripple.com/xrp/market-performance/) reports how much RCP the company has available and locked in escrow at present.

## See Also

- [Send RCP (Interactive Tutorial)](send-xrp.html)
- [List RCP In Your Exchange](list-xrp-in-your-exchange.html)
- [Currency Formatting in RCP APIs](currency-formats.html#)
