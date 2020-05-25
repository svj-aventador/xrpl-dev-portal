# Basic Data Types

Different types of objects are uniquely identified in different ways:

[Accounts](accounts.html) are identified by their [Address][], for example `"r9cZA1mLK5R5Am25ArfXFmqgNwjZgnfk59"`. Addresses always start with "r". Many `rippled` methods also accept a hexadecimal representation.

[Transactions](transaction-formats.html) are identified by a [Hash][] of the transaction's binary format. You can also identify a transaction by its sending account and [Sequence Number][].

Each closed [Ledger](ledger-data-formats.html) has a [Ledger Index][] and a [Hash][] value. When [Specifying Ledgers][] you can use either one.

## Addresses
[Address]: #addresses

{% include '_snippets/data_types/address.md' %}
<!--{#_ #}-->


## Hashes
[Hash]: #hashes

{% include '_snippets/data_types/hash.md' %}
<!--{#_ #}-->

### Hash Prefixes
[[Source]](https://github.com/ripple/rippled/blob/master/src/ripple/protocol/HashPrefix.h "Source")

In many cases, the RCP Ledger prefixes an object's binary data with a 4-byte code before calculating its hash, so that objects of different types have different hashes even if their binary formats are the same. The existing 4-byte codes are structured as three alphabetic characters, encoded as ASCII, followed by a zero byte.

Some types of hash appear in API requests and responses. Others are only calculated as the first step of signing a certain type of data, or calculating a higher-level hash. The following table shows all 4-byte hash prefixes the RCP Ledger uses:

| Object Type                           | API Fields                           | Hash Prefix (Hex) | Hash Prefix (Text) |
|:--------------------------------------|:-------------------------------------|:------------------|:--|
| Consensus proposal                    | N/A                                  | `0x50525000`      | `PRP\0` |
| Ledger Version                        | `ledger_hash`                        | `0x4C575200`      | `LWR\0` |
| Ledger state data                     | `account_state` in [ledger header][] | `0x4D4C4E00`      | `MLN\0` |
| Ledger data inner node                | N/A                                  | `0x4D494E00`      | `MIN\0` |
| Ledger data inner node ([SHAMapv2][]) | N/A                                  | `0x494E5200`      | `INR\0` |
| Payment Channel Claim                 | N/A                                  | `0x434C4D00`      | `CLM\0` |
| Signed Transaction                    | `hash` of transactions               | `0x54584E00`      | `TXN\0` |
| Transaction with metadata             | N/A                                  | `0x534E4400`      | `SND\0` |
| Unsigned Transaction (Single-signing) | N/A                                  | `0x53545800`      | `STX\0` |
| Unsigned Transaction (Multi-signing)  | N/A                                  | `0x534D5400`      | `SMT\0` |
| Validation vote                       | N/A                                  | `0x56414C00`      | `VAL\0` |
| Validator subkey authorization ("validator manifest") | N/A                  | `0x4D414E00`      | `MAN\0` |

[ledger header]: ledger-header.html
[SHAMapv2]: known-amendments.html#shamapv2

[Ledger objects IDs](ledger-object-ids.html) are calculated in a similar way, but they use a 2-byte prefix called a "space key" instead of a prefix in the form described here.


## Account Sequence
[Sequence Number]: #account-sequence

{% include '_snippets/data_types/account_sequence.md' %}
<!--{#_ #}-->


## Ledger Index
[Ledger Index]: #ledger-index

{% include '_snippets/data_types/ledger_index.md' %}
<!--{#_ #}-->


### Specifying Ledgers

Many API methods require you to specify an instance of the ledger, with the data retrieved being considered up-to-date as of that particular version of the shared ledger. The commands that accept a ledger version all work the same way. There are three ways you can specify which ledger you want to use:

1. Specify a ledger by its [Ledger Index][] in the `ledger_index` parameter. Each closed ledger has a ledger index that is 1 higher than the previous ledger. (The very first ledger had ledger index 1.)
2. Specify a ledger by its [Hash][] value in the `ledger_hash` parameter.
3. Specify a ledger by one of the following shortcuts, in the `ledger_index` parameter:
    * `validated` for the most recent ledger that has been validated by the whole network
    * `closed` for the most recent ledger that has been closed for modifications and proposed for validation
    * `current` for the server's current working version of the ledger.

There is also a deprecated `ledger` parameter which accepts any of the above three formats. *Do not* use this parameter; it may be removed without further notice.

If you do not specify a ledger, the `current` (in-progress) ledger is chosen by default. If you provide more than one field specifying ledgers, the deprecated `ledger` field is used first if it exists, falling back to `ledger_hash`. The `ledger_index` field is ignored unless neither of the other two are present.

**Note:** Do not rely on this default behavior for specifying a ledger; it is subject to change. Always specify a ledger version in the request if you can.


## Specifying Currency Amounts

There are two kinds of currencies in the RCP Ledger: RCP, and issued currencies. These two types of currencies are specified in different formats, with different precision and rounding behavior.

Some fields, such as the destination `Amount` of a [Payment transaction][], can be either type. Some fields only accept RCP specifically, such as the `Fee` field ([transaction cost](transaction-cost.html)).

RCP is specified as a string containing an integer number of "drops" of RCP, where 1 million drops equals 1 RCP. Issued currencies are instead specified as an object with fields for the decimal amount, currency code, and issuer. For example:

- **RCP** - To specify an `Amount` field with a value of 13.1 RCP:

        "Amount": "13100000"

- **Issued Currency** - To specify an `Amount` field with a value of 13.1 FOO issued by or to rf1B...:

        "Amount": {
            "value": "13.1",
            "code": "FOO",
            "issuer": "rf1BiGeXwwQoi8Z2ueFYTEXSwuJYfV2Jpn"
        }

For more information, see [Currency Formats](currency-formats.html).


## Specifying Time

The `rippled` server and its APIs represent time as an unsigned integer. This number measures the number of seconds since the "Ripple Epoch" of January 1, 2000 (00:00 UTC). This is like the way the [Unix epoch](http://en.wikipedia.org/wiki/Unix_time) works, except the Ripple Epoch is 946684800 seconds after the Unix Epoch.

Don't convert Ripple Epoch times to UNIX Epoch times in 32-bit variables: this could lead to integer overflows.

<!--{# common link defs #}-->
{% include '_snippets/rippled-api-links.md' %}			
{% include '_snippets/tx-type-links.md' %}			
{% include '_snippets/rippled_versions.md' %}
