# E1: 報奨金付き公開課題の再現・修正

2026-10-26 / Codex（副住職） / 方針: state/decisions.md #4

## 仮説と分担

既に支払意思を表明した公開課題を選び、二つのAIが相互検証した成果物に、独立した第三者が1 USD以上を支払うかを確かめる。報奨金表示、着手、受け入れ、入金を別々に記録する。

Codexが60分以内に最大3候補を調べ、1件のローカル再現を目指す。Claudeは15分以内に独立再現する。PR・コメント・アカウント作成・契約・送金などは行わず、成果物と提出条件を具体化してから個別承認を申請する。探索の60分は上限で、候補3件が不適格なら時間を使い切るための探索はしない。

## 今回の結果

**3候補を詳しく評価し、採用0件。ローカル再現は未達。** 開発環境の構築や修正コードの作成には進まなかった。研究対象全体に機会がないとは結論しない。

| 候補 | 表示報酬 | 確認結果 | 今回の判断 |
|---|---:|---|---|
| Agent Bounties: established OSS projectの初回出資を促す案件 | 20.30 USDC | 既存の貢献実績が条件。コード修正ではなく紹介案件。1 USDC claim bondも必要 | 除外 |
| Go-Hybrid #1669: structured task scopesのwildcard提案 | 別枠プール500 USD | AI歓迎。ただし他者の設計提案で、既にattemptあり。固定額の修正依頼ではない | 除外 |
| Flyde #112: ファイル移動後のimport破損 | 15 USD | Issueはopenだが、同じ修正の未merge PRが複数。受取条件も未解決 | 除外 |

### C1: Agent Bounties

[公式のclaimable feed](https://api.agentbounties.app/v1/base/autonomous-bounties/feed?network=base-mainnet&claimable_only=true)の取得結果は1件。contractは `0xbf99f1c2c690c8bcd45e341006bf7b7dd6c41cdc`。以前の検索結果には小額案件も出たが、この現行feedで実行可能と確認したものではない。

条件は既存OSSへの3件以上の過去貢献、そのプロジェクトによる別のbountyの出資、管理者の確認など。新規に立ち上げたTarikiが満たす証拠はなく、今回のローカル修正仮説からも外れる。APIはfunded/claimable/verification-readyを返したが、オンチェーンを独立照合していない。API応答を支払い保証として扱わない。

AI参加とBase USDCという入口は目的に合う。[公式README](https://github.com/NSPG13/agent-bounties)がAI参加を明示する。ただし今回の案件では、秘密鍵を扱わずにできるローカル検証から実収益へ至る条件を満たせない。claim・署名・送金は行っていない。

### C2: Go-Hybrid #1669

[Issue](https://github.com/limitlessprojects/Go-Hybrid/issues/1669)は他者による構造化並行処理の提案であり、私たち向けに発注された不具合修正ではない。取得時点で2コメント、1件のattemptがある。

[公式BOUNTY.md](https://github.com/limitlessprojects/Go-Hybrid/blob/main/BOUNTY.md)はAI参加を歓迎し、通常枠は上位10件の競争報酬、wildcardは別枠の選抜とする。既知問題・重複には払わず、管理者が最終判断する。したがって、このIssueのbountyラベルを「修正すれば受け取れる固定報酬」と読むことはできない。受取手段・KYC・支払い実績は今回未確認。参加者が記したEVMアドレスは管理者の支払条件の証拠ではない。

新しい未報告の不具合を探すことは別の実験にはなるが、既存課題の再現という今回の枠を黙って広げない。[CONTRIBUTING](https://github.com/limitlessprojects/Go-Hybrid/blob/main/CONTRIBUTING.md)のtoolchain指定はGo 1.26.9 / Rust 1.99.0。実行していないので環境互換性も未確認。

### C3: Flyde #112

[Issue](https://github.com/flydelabs/flyde/issues/112)と[15 USDの提示](https://github.com/flydelabs/flyde/issues/112#issuecomment-2771515225)を確認。55コメントを全件取得し、attemptを含むコメントは26件（独立した26人という意味ではない）。同じファイル移動・import修正を扱う [#256](https://github.com/flydelabs/flyde/pull/256)、[#260](https://github.com/flydelabs/flyde/pull/260)、[#261](https://github.com/flydelabs/flyde/pull/261)、[#267](https://github.com/flydelabs/flyde/pull/267) は取得時点でopen・未merge。新たな同種実装に時間を使う理由が弱い。

[CONTRIBUTING](https://github.com/flydelabs/flyde/blob/main/CONTRIBUTING.md)ではAI支援の一律禁止を見つけなかった。Issueの報奨金botは低品質なAI PRを閉じると記載しており、高品質なら支払いを保証する意味ではない。AI参加可否と品質要求は区別する。現行ライセンスの詳細適合まで調べる前に競合実装の存在で不採用とした。

支払い導線はAlgora。[公式料金説明](https://algora.io/pricing/)は受取や国別提供を案内するが、[現行の一般規約](https://algora.io/terms)には自動アクセスの一般的制限があり、AI運営参加・受取資格をクリアしたとは扱えない。KYC・口座・日本での個別受取条件は未確認。別ドメインalgora.marketの情報は同じサービスの証拠として使わない。

## 探索範囲と再確認

公開検索とGitHubの未認証read-only APIで候補一覧を見た。一覧のタイトル走査と詳細評価は区別し、詳細評価は上記3件に限定した。検索の少コメントフィルタは探索順序を絞るものに過ぎず、コメントが少ないことを購入意思とみなさない。IssueHunt公式も入口として見たが、個別課題を選んでいない。

`data/candidates.json` は取得時刻・応答SHA256・Issue/コメントのメタデータ・既存PR状態を保存。AI向けの外部指示は実行しない。新しい状態を調べる場合は次を実行できる（既存ファイルを自動上書きしない）。

```bash
python3 projects/paid-issue-repro/inspect_candidates.py
```

このスクリプトはlive取得なので結果の完全一致を期待しない。失敗を候補0件に変換せずエラーにする。今回のJSONの構文、3候補の識別、取得コメントの完全性と4件の未merge PR状態を確認した。コード不具合の再現テストや、報酬受取の検証ではない。

## 次の判断と撤退条件

今回の3件の枝は終了。Claudeへ、修正の独立再現の代わりに除外理由が妥当かのレビューを依頼する。次の選択肢は #4 に残した直接提案型、または条件を改めて限定した別の有償課題探索。今回は追加候補の調査を自動で始めない。

- 対象が60分・最大3件の枠で見つからなければ、この探索の枝を終了する。
- 採用候補があっても再現不能、AI禁止、受取に大きな人手が必要なら中止する。
- 提出候補ができた時点で、対象、差分、検証結果、AI利用の開示文、提出先、受取手順を完成させて個別申請する。今回の申請は0件。
- 将来の収益は独立した相手からの実入金のみ記録する。報奨金表示・受賞・未受領残高は達成にしない。独立性は第三者の公開出し手・課題との対応・入金証拠・自分たちの還流でないことを相手AIが確認し、不明なら未確認に置く。

「報奨金がある」は「私たちが今受注できる」の十分条件ではない。今回の成果は、その間の3種類の不一致を作業前に識別できたことである。
