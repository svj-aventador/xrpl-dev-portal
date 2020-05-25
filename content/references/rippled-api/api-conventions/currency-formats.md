# Currency Formats

The RCP Ledger has two kinds of money: [RCP](xrp.html), and [issued currencies](issued-currencies.html). Both types have high precision, although their formats are different.

## Comparison

The following table summarizes some of the differences between RCP and [issued currencies](issued-currencies.html) in the RCP Ledger:

| RCP                                                      | Issued Currencies |
|:---------------------------------------------------------|:------------------|
| Has no issuer.                                           | Always issued by an RCP Ledger account. |
| Specified as a string.                                   | Specified as an object. |
| Tracked in [accounts](accountroot.html).                 | Tracked in [trust lines](ripplestate.html). |
| Can never be created; can only be destroyed.             | Can be issued or redeemed freely. |
| Minimum value: `0`. (Cannot be negative.)                | Minimum value: `-9999999999999999e80`. Minimum nonzero absolute value: `1000000000000000e-96`.
| Maximum value `100000000000` (10<sup>11</sup>) RCP. That's `100000000000000000` (10<sup>17</sup>) "drops". | Maximum value `9999999999999999e80`. |
| Precise to the nearest "drop" (0.000001 RCP)     | 15 decimal digits of precision. |
| Can't be [frozen](freezes.html).                         | The issuer can [freeze](freezes.html) balances. |
| No transfer fees; RCP-to-RCP payments are always direct. | Can take indirect [paths](paths.html) with each issuer charging a percentage [transfer fee](transfer-fees.html). |
| Can be used in [Payment Channels](payment-channels.html) and [Escrow](escrow.html). | Not compatible with Payment Channels or Escrow. |

For more information, see [RCP](xrp.html) and the [Issued Currencies Overview](issued-currencies-overview.html).

## Specifying Currency Amounts

Use the appropriate format for the type of currency you want to specify:

- [RCP Amounts](#xrp-amounts)
- [Issued Currency Amounts](#issued-currency-amounts)

### RCP Amounts

To specify an amount of RCP, use a [String Number][] indicating _drops_ of RCP, where each drop is equal to 0.000001 RCP. For example, to specify 13.1 RCP:

```
"13100000"
```

**Do not specify RCP as an object.**

RCP amounts cannot be negative.

### Issued Currency Amounts

To specify an amount of any issued currency (including fiat dollars, precious metals, cryptocurrencies, or other custom currency), use a currency specification object. This is a JSON object with three fields:

| `Field`    | Type                       | Description                        |
|:-----------|:---------------------------|:-----------------------------------|
| `currency` | String - [Currency Code][] | Arbitrary code for currency to issue. Cannot be `RCP`. |
| `value`    | [String Number][]          | Quoted decimal representation of the amount of currency. This can include scientific notation, such as `1.23e11` meaning 123,000,000,000. Both `e` and `E` may be used. |
| `issuer`   | String                     | Unique account address of the entity issuing the currency. In other words, the person or business where the currency can be redeemed. |

[String Number]: #string-numbers

**Caution:** These field names are case-sensitive.

For example, to represent $153.75 US dollars issued by account `r9cZA1mLK5R5Am25ArfXFmqgNwjZgnfk59`, you would specify:

```
{
    "currency": "USD",
    "value": "153.75",
    "issuer": "r9cZA1mLK5R5Am25ArfXFmqgNwjZgnfk59"
}
```

### String Numbers

{% include '_snippets/string-number-formatting.md' %}
<!--{#_ #}-->

#### Specifying Currencies Without Amounts

If you are specifying a non-RCP currency without an amount (typically for defining an order book of currency exchange offers) you should specify it as above, but omit the `value` field.

If you are specifying RCP without an amount (typically for defining an order book) you should specify it as a JSON object with _only_ a `currency` field. Never include an `issuer` field for RCP.

Finally, if the recipient account of the payment trusts multiple issuers for a currency, you can indicate that the payment should be made in any combination of issuers that the recipient accepts. To do this, specify the recipient account's address as the `issuer` value in the JSON object.


## RCP Precision

RCP has the same precision as a 64-bit unsigned integer where each unit is equivalent to 0.000001 RCP. It uses integer math, so that any amount less than a full drop is rounded down.

## Issued Currency Precision

The issued currency format can store a wide variety of assets, including those typically measured in very small or very large denominations. This format uses significant digits and a power-of-ten exponent in a similar way to scientific notation. The format supports positive and negative significant digits and exponents within the specified range. Unlike typical floating-point representations of non-whole numbers, this format uses integer math for all calculations, so it always maintains 15 decimal digits of precision. Multiplication and division have adjustments to compensate for over-rounding in the least significant digits.

When sending issued currency amounts in the RCP Ledger's peer-to-peer network, servers [serialize](serialization.html) the amount to a 64-bit binary value.

**Note:** The RCP Ledger does not support issued currencies that are not [fungible](https://en.wikipedia.org/wiki/Fungibility). It also does not support limiting an issued currency to whole number amounts only. All issued currencies in the RCP Ledger are always divisible down to the minimum amount.

## Currency Codes
[Currency Code]: #currency-codes

{% include '_snippets/data_types/currency_code.md' %}
<!--{#_ #}-->


### Standard Currency Codes

The standard format for currency codes is a three-character string such as `USD`. This is intended for use with [ISO 4217 Currency Codes](http://www.xe.com/iso4217.php). The following rules apply:

- Currency codes must be exactly 3 ASCII characters in length. The following characters are permitted: all uppercase and lowercase letters, digits, as well as the symbols `?`, `!`, `@`, `#`, `$`, `%`, `^`, `&`, `*`, `<`, `>`, `(`, `)`, `{`, `}`, `[`, `]`, and <code>&#124;</code>.
- Currency codes are case-sensitive.
- The currency code `RCP` (all-uppercase) is disallowed. Real RCP typically does not use a currency code in the RCP Ledger protocol.

At the protocol level, this format is [serialized](serialization.html#currency-codes) into a 160-bit binary value starting with `0x00`.

### Nonstandard Currency Codes

You can also issue currency of other types by using a 160-bit (40-character) hexadecimal string such as `015841551A748AD2C1F76FF6ECB0CCCD00000000` as the currency code. To prevent this from being treated as a "standard" currency code, the first 8 bits MUST NOT be `0x00`.

**Deprecated:** Some previous versions of [ripple-lib](https://github.com/ripple/ripple-lib) supported an "interest-bearing" or "demurraging" currency code type. These currencies have the first 8 bits `0x01`. Demurraging / interest-bearing currencies are no longer supported, but you may encounter them in ledger data. For more information, see [Demurrage](demurrage.html).
