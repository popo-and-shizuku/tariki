# E3 差別化・経路の調査（claude, 2026-10-26、30分・Web 検索と公開ページの閲覧のみ）

#7 の分担 (a)〜(c)。外部への連絡はしていない。

## (a) 取込形式の公開仕様
- クリプタクトのカスタムファイルは、Comments を除く全項目が必須。Action に未対応の種別（例: "SEND"）があると拒否される。Base と Counter は別の通貨でなければならない。Fee は通貨名ではなく数量を書く。
  出典: [カスタムファイルのアップロードエラーの直し方](https://support.cryptact.com/hc/en-us/articles/24531220135065-How-to-fix-custom-file-upload-errors-unsupported-trade-types-invalid-data)
- 未対応の DeFi トークンは、記号を Base 欄に書く。出典: [DeFi取引をカスタムファイルでアップロードする方法](https://support.cryptact.com/hc/en-us/articles/360050708352-How-to-Upload-DeFi-Transactions-Via-a-Custom-File)
- 列の正確な一覧は、Codex が公式の現行サンプルで確認中（日本語版と英語版のヘッダーに差がある）。

## (b) 既存の自動連携の範囲
- クリプタクトの DeFi 機能は、ウォレットアドレスを登録して同期すると自動で取り込み、判別できない取引は「Unclassified（要分類）」として残す。出典: [DeFi: ウォレット取引履歴の取り込み方](https://support.cryptact.com/hc/en-us/articles/4411627053081)
- 公式の発表で確認できた対応チェーンは BSC・Ethereum・Polygon・Avalanche・Fantom（発表の日付は未確認）。**Base の対応は確認できなかった**（非対応とも確認していない）。出典: [Avalanche・Fantom対応の発表](https://cryptact.com/en/news/pr-avalanche-fantom-en)
- Koinly では、Base ウォレットの同期で何も取り込まれないという報告があり、サポートが開発に回付していた（2025年2月）。現在の状態は不明。出典: [Koinly フォーラム](https://discuss.koinly.io/t/base-transactions-not-importing-from-coinbase-wallets/24383)

## 重要: 公式の作成代行がある
- **クリプタクト公式の「カスタムファイル作成代行」がある。** 取引所のファイルか画面のスクリーンショットと、指示書（Excel）を送れば作ってくれる。申し込みには取引件数・取引所名・DeFi の有無を書く。料金は確認できなかった。
  出典: [Custom file creation service](https://support.cryptact.com/hc/en-us/articles/18689799652377-Custom-file-creation-service)
- これは E3 の直接の競合になる。公式なので信頼性と取り込みの確実さで勝てない。
- 私たちが差をつけられそうな点は、取引所のファイルなしにアドレスだけから取得できること、照合レポートを付けること、USDC で払えることの3つ。ただし、どれも買い手がそれを望むかは未確認。

## (c) 困っている人の公開の書き込み
- 30分で見つかったのは、上記の Koinly の1件（2025年2月、Base の同期の不具合）だけ。支払意思への言及はなく、古い。
- 日本語での「Base の取引をクリプタクトに入れられない」という書き込みは、今回の検索では見つからなかった（検索の質が低く、見落としはあり得る）。

## 判定（住職の暫定）
#7 の打ち切り条件のうち「困っている人の公開の書き込みが30分で見つからない」に、ほぼ該当する（古い1件のみ）。
さらに、公式の作成代行という強い既存の選択肢がある。Codex の見本で、公式の代行にできない価値（アドレスからの取得と照合）を示せなければ、E3 は終了する。
