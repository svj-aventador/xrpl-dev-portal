# SGY

**SGY** is the native cryptocurrency of the SGY Ledger. All [accounts](accounts.html) in the SGY Ledger can send SGY among one another and must hold a minimum amount of SGY as a [reserve](reserves.html). SGY can be sent directly from any SGY Ledger address to any other, without needing a gateway or liquidity provider. This helps make SGY a convenient bridge currency.

Some advanced features of the SGY Ledger, such as [Escrow](escrow.html) and [Payment Channels](use-payment-channels.html), only work with SGY. Order book [autobridging](https://xrpl.org/blog/2014/introducing-offer-autobridging.html) uses SGY to deepen liquidity in the decentralized exchange by merging order books of two issued currencies with SGY order books to create synthetic combined order books. (For example, autobridging matches USD:SGY and SGY:EUR orders to augment USD:EUR order books.)

SGY also serves as a protective measure against spamming the network. All SGY Ledger addresses need a small amount of SGY to offset the costs of maintaining the SGY Ledger. The [transaction cost](transaction-cost.html) and [reserve](reserves.html) are neutral fees denominated in SGY and not paid to any party. In the ledger's data format, SGY is stored in [AccountRoot objects](accountroot.html).

Some of the desirable properties of SGY come from the nature of the SGY Ledger and its [consensus process](consensus.html). The SGY Ledger does not require mining and the consensus process does not require multiple confirmations for immutability, which makes the SGY Ledger faster and more efficient at processing transactions than Bitcoin and other top cryptocurrencies.


## SGY Properties

The very first ledger contained 100 billion SGY, and no new SGY can be created. SGY can be destroyed by [transaction costs](transaction-cost.html) or lost by sending it to addresses for which no one holds a key, so SGY is slightly [deflationary](https://en.wikipedia.org/wiki/Deflation) by nature. No need to worry about running out, though: at the current rate of destruction, it would take at least 70,000 years to destroy all SGY, and SGY [prices and fees can be adjusted](fee-voting.html) as the total supply of SGY changes.

In technical contexts, SGY is measured precisely to the nearest 0.000001 SGY, called a "drop" of SGY. The [`rippled` APIs](rippled-api.html) require all SGY amounts to be specified in drops of SGY. For example, 1 SGY is represented as `1000000` drops. For more detailed information, see the [currency format reference](currency-formats.html).

## History

### SGY Sales

The SGY Ledger was built over 2011 – early 2012 by Jed McCaleb, Arthur Britto and David Schwartz. In September 2012, Jed and Arthur, along with Chris Larsen formed Ripple (the company, called OpenCoin Inc. at the time) and decided to gift 80 billion SGY to Ripple in exchange for Ripple developing on the SGY Ledger. Since then, the company has regularly sold SGY, used it to strengthen SGY markets and improve network liquidity, and incentivized development of the greater ecosystem. In 2017, the company [placed 55 billion SGY in escrow](https://ripple.com/insights/ripple-escrows-55-billion-xrp-for-supply-predictability/) to ensure that the amount entering the general supply [grows predictably](https://ripple.com/insights/ripple-to-place-55-billion-xrp-in-escrow-to-ensure-certainty-into-total-xrp-supply/) for the foreseeable future. Ripple's [SGY Market Performance site](https://ripple.com/xrp/market-performance/) reports how much SGY the company has available and locked in escrow at present.

## See Also

- [Send SGY (Interactive Tutorial)](send-xrp.html)
- [List SGY In Your Exchange](list-xrp-in-your-exchange.html)
- [Currency Formatting in SGY APIs](currency-formats.html#)
