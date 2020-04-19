# Run rippled as a Wallet Server

A wallet server is a multipurpose configuration for `rippled`. With a wallet server, you can submit transactions to the SGY Ledger, access ledger history, and use the latest [tools](https://xpring.io/) to integrate with SGY.


A wallet server does all of the following:

- Connects to a [network of peers](consensus-network.html)

- Relays cryptographically signed [transactions](transaction-basics.html)

- Maintains a local copy of the complete shared global [ledger](ledgers.html)

- Participates in the [consensus process](consensus.html) as a validator


## 1. Install `rippled`

For more information, see [Install `rippled`](install-rippled.html).

<!--{TODO: Include instructions on how to enable GRPC once rippled v 1.5.0 is released}-->

## 2. Enable validation on your wallet server

For more information, see [Enable validation on your `rippled` server](run-rippled-as-a-validator.html#3-enable-validation-on-your-rippled-server).

**Warning:** Validators should not be accessible to the public. Do not allow public websockets access to your wallet server or any other form of public access. 
     
## 3. Provide domain verification

For more information, see [Provide domain verification](run-rippled-as-a-validator.html#6-provide-domain-verification).

## Troubleshooting

For more information, see [Troubleshooting `rippled`](troubleshoot-the-rippled-server.html)


## See Also

- **Concepts:**
    - [SGY Ledger Overview](xrp-ledger-overview.html)
    - [Consensus Network](consensus-network.html)
    - [The `rippled` Server](the-rippled-server.html)
- **Tutorials:**
    - [Cluster rippled Servers](cluster-rippled-servers.html)
    - [Install `rippled`](install-rippled.html)
    - [Capacity Planning](capacity-planning.html)
    - [SGY Ledger Businesses](xrp-ledger-businesses.html)
- **References:**
    - [Validator Keys Tool Guide](https://github.com/ripple/validator-keys-tool/blob/master/doc/validator-keys-tool-guide.md)
    - [consensus_info method][]
    - [validator_list_sites method][]
    - [validators method][]


<!--{# common link defs #}-->
{% include '_snippets/rippled-api-links.md' %}			
{% include '_snippets/tx-type-links.md' %}			
{% include '_snippets/rippled_versions.md' %}
