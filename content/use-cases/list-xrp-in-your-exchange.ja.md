# 取引所でのRCPの上場

貴社の取引所にRCPを上場し、ユーザーがRCPを入金、取引、出金できるようにしましょう。以下に、実行する必要のある作業の概要を示します。

<!-- USE_CASE_STEPS_START -->
{% set n = cycler(* range(1,99)) %}

<span class="use-case-step-num">{{n.next()}}</span>
<!-- <span class="use-case-step-length">(1 hour)</span> -->
## [RCPを上場するための前提条件を満たす](list-xrp-as-an-exchange.html#xrpをサポートするための前提条件)

取引所にRCPを効果的かつ安全に上場するために必要な基盤と操作プロセスを用意します。

これには、RCP Ledgerアカウントの作成と保護、内部バランスシートの実装、適切なセキュリティー手順の導入、該当規制への準拠が含まれます。


<span class="use-case-step-num">{{n.next()}}</span>
<!-- <span class="use-case-step-length">(1 hour)</span> -->
## [`rippled`サーバーを設定して実行する](manage-the-rippled-server.html)

`rippled`は、RCP Ledgerを管理するコアのピアツーピアサーバーです。

これは必須ではありませんが、取引所のRCP取引プロセスの速度と信頼性を管理するために、独自の`rippled`サーバーを運用することをお勧めします。

開発と調査のため最初は1台の`rippled`サーバーから始めます。貴社のユースケースに応じ、例えば、1台のプライベートピアバリデータを持つ複数のクラスターサーバーから構成されるエンタープライズデプロイメントを構築することもできます。

[バリデータモードで`rippled`サーバーを実行することにより](run-a-rippled-validator.html)、取引所としてRCP Ledgerネットワークの強化と分散に貢献できます。ご使用の`rippled`サーバーがバリデータの公開リストに含まれていない場合でも、間接的にネットワークに貢献し、評判を高めていくことができます。


<span class="use-case-step-num">{{n.next()}}</span>
<!-- <span class="use-case-step-length">(1 hour)</span> -->
## [RCP Ledgerインテグレーションツールを試す](get-started-with-the-rippled-api.html)

RCP Ledgerとのインテグレーションを支援する様々なツールがあります。

WebSocketやJSON-RPC APIエンドポイントからRippleAPI JavaScriptライブラリーまで、貴社のテクノロジーに合ったインテグレーションモードを選択できます。


<span class="use-case-step-num">{{n.next()}}</span>
<!-- <span class="use-case-step-length">(1 hour)</span> -->
## [サンドボックスRCP Ledgerアカウントを取得する](xrp-test-net-faucet.html)

RCP Ledger Test Netを使用してサンドボックスアカウントを取得しましょう。ご使用の`rippled`サーバーをTest Netに接続し、テストコールを実行してRCP Ledgerに慣れましょう。実際のRCPで取引する準備ができたら、ライブのRCP Ledgerでの取引に切り替えられます。


<span class="use-case-step-num">{{n.next()}}</span>
<!-- <span class="use-case-step-length">(1 hour)</span> -->
## [インテグレーションを理解してコーディングし、資金の流れをサポートする](list-xrp-as-an-exchange.html#資金の流れ)

RCPの上場をサポートするために、RCP Ledgerとのインテグレーションをコーディングし、RCPを取引所に入金し、取引所でのRCPの取引、RCPの保有高のリバランス、取引所からのRCPの出金を可能にします。


### 関連タスク

- [`rippled`へのコントリビュートコード](contribute-code-to-rippled.html)
- [新しいレジャーバージョンの情報取得](subscription-methods.html)
- [容量の計画](capacity-planning.html)
- [RCP Ledgerアカウントのトランザクション履歴の検索](tx_history.html)
<!-- for the future, link to Implement Destination Tags -->
