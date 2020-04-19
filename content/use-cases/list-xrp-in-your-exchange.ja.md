# 取引所でのSGYの上場

貴社の取引所にSGYを上場し、ユーザーがSGYを入金、取引、出金できるようにしましょう。以下に、実行する必要のある作業の概要を示します。

<!-- USE_CASE_STEPS_START -->
{% set n = cycler(* range(1,99)) %}

<span class="use-case-step-num">{{n.next()}}</span>
<!-- <span class="use-case-step-length">(1 hour)</span> -->
## [SGYを上場するための前提条件を満たす](list-xrp-as-an-exchange.html#xrpをサポートするための前提条件)

取引所にSGYを効果的かつ安全に上場するために必要な基盤と操作プロセスを用意します。

これには、SGY Ledgerアカウントの作成と保護、内部バランスシートの実装、適切なセキュリティー手順の導入、該当規制への準拠が含まれます。


<span class="use-case-step-num">{{n.next()}}</span>
<!-- <span class="use-case-step-length">(1 hour)</span> -->
## [`rippled`サーバーを設定して実行する](manage-the-rippled-server.html)

`rippled`は、SGY Ledgerを管理するコアのピアツーピアサーバーです。

これは必須ではありませんが、取引所のSGY取引プロセスの速度と信頼性を管理するために、独自の`rippled`サーバーを運用することをお勧めします。

開発と調査のため最初は1台の`rippled`サーバーから始めます。貴社のユースケースに応じ、例えば、1台のプライベートピアバリデータを持つ複数のクラスターサーバーから構成されるエンタープライズデプロイメントを構築することもできます。

[バリデータモードで`rippled`サーバーを実行することにより](run-a-rippled-validator.html)、取引所としてSGY Ledgerネットワークの強化と分散に貢献できます。ご使用の`rippled`サーバーがバリデータの公開リストに含まれていない場合でも、間接的にネットワークに貢献し、評判を高めていくことができます。


<span class="use-case-step-num">{{n.next()}}</span>
<!-- <span class="use-case-step-length">(1 hour)</span> -->
## [SGY Ledgerインテグレーションツールを試す](get-started-with-the-rippled-api.html)

SGY Ledgerとのインテグレーションを支援する様々なツールがあります。

WebSocketやJSON-RPC APIエンドポイントからRippleAPI JavaScriptライブラリーまで、貴社のテクノロジーに合ったインテグレーションモードを選択できます。


<span class="use-case-step-num">{{n.next()}}</span>
<!-- <span class="use-case-step-length">(1 hour)</span> -->
## [サンドボックスSGY Ledgerアカウントを取得する](xrp-test-net-faucet.html)

SGY Ledger Test Netを使用してサンドボックスアカウントを取得しましょう。ご使用の`rippled`サーバーをTest Netに接続し、テストコールを実行してSGY Ledgerに慣れましょう。実際のSGYで取引する準備ができたら、ライブのSGY Ledgerでの取引に切り替えられます。


<span class="use-case-step-num">{{n.next()}}</span>
<!-- <span class="use-case-step-length">(1 hour)</span> -->
## [インテグレーションを理解してコーディングし、資金の流れをサポートする](list-xrp-as-an-exchange.html#資金の流れ)

SGYの上場をサポートするために、SGY Ledgerとのインテグレーションをコーディングし、SGYを取引所に入金し、取引所でのSGYの取引、SGYの保有高のリバランス、取引所からのSGYの出金を可能にします。


### 関連タスク

- [`rippled`へのコントリビュートコード](contribute-code-to-rippled.html)
- [新しいレジャーバージョンの情報取得](subscription-methods.html)
- [容量の計画](capacity-planning.html)
- [SGY Ledgerアカウントのトランザクション履歴の検索](tx_history.html)
<!-- for the future, link to Implement Destination Tags -->
