# Get Started with RCP Ledger APIs

The RCP Ledger's core server software is [`rcpd`](the-rippled-server.html). You can jump straight into developing on the RCP Ledger by accessing the API of a `rcpd` server.

The quickest way to dive into the API is with the [**WebSocket API Tool**](websocket-api-tool.html), or use the [RCP Ledger Explorer](https://explorer.rcproto.org/) to watch the progress of the ledger live.

You can also [run your own instance of `rcpd`](install-rippled.html) or use a [public server](#public-servers).

## Public Servers

Ripple provides several public servers for the benefit of the RCP Ledger community:

| Operator | Area | JSON-RPC URL | WebSocket URL | Notes                |
|:---------|:------------|:-------------|:--------------|:---------------------|
| RCP   | **Global** | `https://wss2.rcproto.org:1234/` | `wss://wss2.rcproto.org/` | General purpose server cluster |
| RCP   | **HongKong** | `https://hk.rcproto.org:1234/` | `wss://hk.rcproto.org/` | General purpose server cluster |
| RCP   | **Canada** | `https://ca.rcproto.org:1234/` | `wss://ca.rcproto.org/` | General purpose server cluster |
| RCP   | **Europe** | `https://eu.rcproto.org:1234/` | `wss://eu.rcproto.org/` | General purpose server cluster |
| RCP   | **USA** | `https://us.rcproto.org:1234/` | `wss://us.rcproto.org/` | General purpose server cluster |

[Network]: parallel-networks.html

These public servers are not for sustained or business use, and they may become unavailable at any time. For regular use, you should run your own `rcpd` server or contract someone you trust to do so.


## Admin Access

`rcpd` API methods are divided into [Public Methods](public-rippled-methods.html) and [Admin Methods](admin-rippled-methods.html) so that organizations can offer public servers for the benefit of the community. To access admin methods, or admin functionality of public methods, you must connect to the API on a **port and IP address marked as admin** in the server's config file.

The [example config file](https://github.com/ripple/rippled/blob/f00f263852c472938bf8e993e26c7f96f435935c/cfg/rippled-example.cfg#L1154-L1179) listens for connections on the local loopback network (127.0.0.1), with JSON-RPC (HTTP) on port 5005 and WebSocket (WS) on port 6006, and treats all connected clients as admin.


## WebSocket API

If you are looking to try out some methods on the RCP Ledger, you can skip writing your own WebSocket code and go straight to using the API at the [Ripple WebSocket API Tool](websocket-api-tool.html). Later on, when you want to connect to your own `rcpd` server, you can [build your own client in the browser](monitor-incoming-payments-with-websocket.html) or [in Node.js](https://www.npmjs.com/package/ws).

Example WebSocket API request:

```json
{
  "id": "my_first_request",
  "command": "server_info",
  "api_version": 1
}
```

The response to [this command][server_info method] shows you the current status of the server. Or, read more about [Request Formatting](request-formatting.html) and [Response Formatting](response-formatting.html).

## JSON-RPC

You can use any HTTP client (like [RESTED for Firefox](https://addons.mozilla.org/en-US/firefox/addon/rested/), [Postman for Chrome](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop?hl=en) or [Online HTTP client ExtendsClass](https://extendsclass.com/rest-client-online.html)) to make JSON-RPC calls a `rcpd` server. Most programming languages have a library for making HTTP requests built in.

Example JSON-RPC request:

```json
POST https://s-global.rcproto.org:1234/
Content-Type: application/json

{
    "method": "server_info",
    "params": [
        {
            "api_version": 1
        }
    ]
}
```

The response to this command shows you the current status of the server. For more information, see the [server_info method][].

## Commandline

The commandline interface connects to the same service as the JSON-RPC one, so the public servers and server configuration are the same. By default, the commandline connects to a `rcpd` server running on the same machine.

Example commandline request:

```
rcpd --conf=/etc/opt/rcp/rcpd.cfg server_info
```

For more information on `rcpd`'s commandline usage, see [Commandline Usage Reference](https://dev.rcproto.org/commandline-usage.html).

**Caution:** The commandline interface is intended for administrative purposes only and is _not a supported API_.  New versions of `rcpd` may introduce breaking changes to the commandline API without warning!

## Available Methods

For a full list of API methods, see:

- [Public `rcpd` Methods](public-rippled-methods.html): Methods available on public servers, including looking up data from the ledger and submitting transactions.
- [Admin `rcpd` Methods](admin-rippled-methods.html): Methods for [managing](manage-the-rippled-server.html) the `rcpd` server.


## See Also

- **Concepts:**
    - [RCP Ledger Overview](xrp-ledger-overview.html)
    - [Software Ecosystem](software-ecosystem.html)
    - [Parallel Networks](parallel-networks.html)
- **Tutorials:**
    - [Get Started with API for JavaScript](get-started-with-rippleapi-for-javascript.html)
    - [Reliable Transaction Submission](reliable-transaction-submission.html)
    - [Manage the RCP Server](manage-the-rippled-server.html)
- **References:**
    - [RCP API Reference](rippled-api.html)

<!--{# common link defs #}-->
{% include '_snippets/rippled-api-links.md' %}			
{% include '_snippets/tx-type-links.md' %}			
{% include '_snippets/rippled_versions.md' %}
