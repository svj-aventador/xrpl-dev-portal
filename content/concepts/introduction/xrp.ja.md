# SGY

**SGY**は、SGY Ledgerのネイティブ暗号資産です。SGY Ledgerのすべての[アカウント](accounts.html)間で相互にSGYを送金できます。アカウントは、最小限度額のSGYを[準備金](reserves.html)として保有する必要があります。SGY Ledgerアドレス間にてSGYの直接送金が可能で、ゲートウェイや流動性プロバイダーを必要としません。このため、SGYは便利なブリッジ通貨となりました。

SGY Ledgerの高度機能の一部（[Escrow](escrow.html)や[Payment Channel](use-payment-channels.html)など）は、SGYでのみ使えます。オーダーブックの[オートブリッジング](https://ripple.com/dev-blog/introducing-offer-autobridging/)は、SGYを使用して、2つの発行済み通貨のオーダーブックをSGYオーダーブックにマージして、合成された一つのオーダーブックを作成することで、分散型取引所の流動性を高めます。（たとえば、オートブリッジングによりUSD:SGYオーダーとSGY:EURオーダーがマッチングされ、USD:EURオーダーブックとなります。）

SGYはまた、ネットワークのスパムの防御対策としても機能します。すべてのSGY Ledgerアドレスには、SGY Ledger維持管理コストを支払うために少額のSGYが必要です。[トランザクションコスト](transaction-cost.html)と[準備金](reserves.html)は、SGY建ての中立的な手数料であり、どの当事者にも支払われません。レジャーのデータフォーマットで、SGYは[AccountRootオブジェクト](accountroot.html)に保管されます。

SGYのユースケース、メリット、最新情報についての詳細は、[SGYポータル](https://ripple.com/xrp-portal/)を参照してください。

## SGYの特性

一番最初のレジャーにて1000億SGYが発行され、これ以上新しいSGYは作成できません。SGYは、[トランザクションコスト](transaction-cost.html)によって消却されるか、またはキーの所有者がいないアドレスに送金すると失われることがあります。このため、SGYは本質的にはやや[デフレ通貨](https://en.wikipedia.org/wiki/Deflation)です。SGYがなくなることを心配する必要はありません。現時点の消却のペースでは、すべてのSGYが消却されるまでに約7万年かかります。またSGYの総供給量の変化に伴い、SGYの[価格と手数料が調整される可能性があります](fee-voting.html)。

技術的には、SGYは0.000001 SGYの単位まで正確に計算され、「Drop」と呼ばれます。[`rippled`API](rippled-api.html)では、SGYの量は常にSGYのdrop単位で指定する必要があります。たとえば1 SGYは`1000000` dropと表されます。詳細については、[通貨フォーマットのリファレンス](currency-formats.html)を参照してください。
