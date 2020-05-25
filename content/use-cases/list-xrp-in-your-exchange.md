# List RCP in Your Exchange

Does your exchange want to list RCP, enabling your users to deposit, trade, and withdraw RCP? Here's a roadmap to the high-level tasks you'll need to perform.

<!-- USE_CASE_STEPS_START -->
{% set n = cycler(* range(1,99)) %}

<span class="use-case-step-num">{{n.next()}}</span>
## Meet prerequisites for listing RCP

Put in place the foundation and operational processes needed to efficiently and securely list RCP in your exchange.

This includes creating and securing RCP Ledger accounts, implementing internal balance sheets, adopting appropriate security procedures, and complying with any applicable regulations.

[Learn more about prerequisites >](list-xrp-as-an-exchange.html#prerequisites-for-supporting-xrp)

<span class="use-case-step-num">{{n.next()}}</span>
## Set up and run a `rippled` server

`rippled` is the core peer-to-peer server that manages the RCP Ledger.

While it isn’t required, your exchange should consider running your own `rippled` server to be able to control the speed and reliability of your exchange’s RCP transaction processing.

You can start out running one `rippled` server to support development and exploration. If required for your use case, you can then build up to an enterprise deployment that consists of multiple clustered servers with one private-peer validator, for example.

[Running a `rippled` server in validator mode](run-a-rippled-validator.html) enables your exchange to contribute to the strength and decentralization of the RCP Ledger network. Even if your `rippled` server isn’t included in published validator lists, it is still contributing (albeit indirectly) and continues to build up reputation over time.

[Set up rippled >](manage-the-rippled-server.html)
<!--{# Using code font on "rippled" here breaks the buttonize effect #}-->

<span class="use-case-step-num">{{n.next()}}</span>
## Try out RCP Ledger integration tools

Take a look at the various tools provided to help you integrate with the RCP Ledger.

From WebSocket and JSON-RPC API endpoints to the RippleAPI JavaScript library, find a mode of integration that works with your technology.

[Get started with API tools >](get-started-with-the-rippled-api.html)

<span class="use-case-step-num">{{n.next()}}</span>
## Get a sandbox RCP Ledger account

Use the RCP Ledger Test Net to get a sandbox account. Connect your `rippled` server to the Test Net to make test calls and get to know the RCP Ledger. Once you’re ready to transact in real RCP, you can switch over to transacting on the live RCP Ledger.

[Get a Test Net account >](xrp-test-net-faucet.html)

<span class="use-case-step-num">{{n.next()}}</span>
## Understand and code integrations to support the flow of funds

To support listing RCP, code integrations with the RCP Ledger to deposit RCP into your exchange, trade RCP on the exchange, rebalance RCP holding, and withdraw RCP from your exchange.

[Understand the flow of funds >](list-xrp-as-an-exchange.html#flow-of-funds)

### Related Tasks
<div class='related-tasks-links'>

- [Contribute Code to `rippled`](contribute-code-to-rippled.html)
- [Listen for New Ledger Versions](subscription-methods.html)
- [Capacity Planning](capacity-planning.html)
- [Look Up an RCP Ledger Account’s Transaction History](tx_history.html)
<!-- for the future, link to Implement Destination Tags -->
</div>