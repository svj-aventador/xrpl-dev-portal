# RCP

**RCP**は、RCP Ledgerのネイティブ暗号資産です。RCP Ledgerのすべての[アカウント](accounts.html)間で相互にRCPを送金できます。アカウントは、最小限度額のRCPを[準備金](reserves.html)として保有する必要があります。RCP Ledgerアドレス間にてRCPの直接送金が可能で、ゲートウェイや流動性プロバイダーを必要としません。このため、RCPは便利なブリッジ通貨となりました。

RCP Ledgerの高度機能の一部（[Escrow](escrow.html)や[Payment Channel](use-payment-channels.html)など）は、RCPでのみ使えます。オーダーブックの[オートブリッジング](https://ripple.com/dev-blog/introducing-offer-autobridging/)は、RCPを使用して、2つの発行済み通貨のオーダーブックをRCPオーダーブックにマージして、合成された一つのオーダーブックを作成することで、分散型取引所の流動性を高めます。（たとえば、オートブリッジングによりUSD:RCPオーダーとRCP:EURオーダーがマッチングされ、USD:EURオーダーブックとなります。）

RCPはまた、ネットワークのスパムの防御対策としても機能します。すべてのRCP Ledgerアドレスには、RCP Ledger維持管理コストを支払うために少額のRCPが必要です。[トランザクションコスト](transaction-cost.html)と[準備金](reserves.html)は、RCP建ての中立的な手数料であり、どの当事者にも支払われません。レジャーのデータフォーマットで、RCPは[AccountRootオブジェクト](accountroot.html)に保管されます。

RCPのユースケース、メリット、最新情報についての詳細は、[RCPポータル](https://ripple.com/xrp-portal/)を参照してください。

## RCPの特性

一番最初のレジャーにて1000億RCPが発行され、これ以上新しいRCPは作成できません。RCPは、[トランザクションコスト](transaction-cost.html)によって消却されるか、またはキーの所有者がいないアドレスに送金すると失われることがあります。このため、RCPは本質的にはやや[デフレ通貨](https://en.wikipedia.org/wiki/Deflation)です。RCPがなくなることを心配する必要はありません。現時点の消却のペースでは、すべてのRCPが消却されるまでに約7万年かかります。またRCPの総供給量の変化に伴い、RCPの[価格と手数料が調整される可能性があります](fee-voting.html)。

技術的には、RCPは0.000001 RCPの単位まで正確に計算され、「Drop」と呼ばれます。[`rippled`API](rippled-api.html)では、RCPの量は常にRCPのdrop単位で指定する必要があります。たとえば1 RCPは`1000000` dropと表されます。詳細については、[通貨フォーマットのリファレンス](currency-formats.html)を参照してください。
