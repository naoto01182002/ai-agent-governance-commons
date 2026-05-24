# Public Launch Plan v1.0 Public Draft

## 1. 基本方針

AI Agent Governance Commons v1.0 Public Draft は、GitHubを正本、note、X、LinkedInを入口、Zenn、Qiita、GitHub Pagesを後続導線として公開する。

GitHubだけでは標準文書として管理しやすいが、読者に届きにくい。noteやSNSだけでは背景は伝わるが、RFP、設計書、監査ログ、RACI、Self-Assessmentへ転記できる正本としては弱い。

したがって、初回公開では以下の役割分担を採用する。

| 場所 | 役割 | 初回公開での扱い |
| --- | --- | --- |
| GitHub Public Repo | 正本、標準文書、テンプレート配布 | 必須 |
| GitHub Releases | バージョン固定 | 必須 |
| note | 背景、思想、問題提起 | 必須 |
| X | 公開告知、初期反応 | 必須 |
| LinkedIn | 企業、SIer、情シス、監査、法務向け告知 | 推奨 |
| Zenn | 技術者、SIer向け実務解説 | 後続 |
| Qiita | 実装、業務システム寄りの解説 | 後続 |
| GitHub Pages | 読みやすいWeb版 | 後続 |
| Speaker Deck等 | 登壇、説明用スライド | 後続 |

## 2. 初回公開順序

| 順番 | 作業 | 目的 |
| --- | --- | --- |
| 1 | 公開用GitHub repo `ai-agent-governance-commons` を作る | 正本を置く |
| 2 | private repoから公開対象だけコピーする | 秘密情報、作業ログ、内部メモの混入を防ぐ |
| 3 | `v1.0 Public Draft` 表記を確認する | 外部向け表示を統一する |
| 4 | GitHub Release `v1.0.0-public-draft` を作る | バージョンを固定する |
| 5 | note記事を公開する | 背景と思想を伝える |
| 6 | XとLinkedInで告知する | 初期反応と実務者の接点を作る |
| 7 | Zenn、Qiita記事を追加する | 技術者、SIer向けに具体化する |
| 8 | GitHub Pages化を検討する | 読みやすいWeb版を作る |

## 3. 初回公開で絞る媒体

初回公開は、以下の3系統に絞る。

| 媒体 | 理由 |
| --- | --- |
| GitHub Public Repo | 正本、差分管理、テンプレート配布に向く |
| note | なぜ必要かを説明しやすい |
| X / LinkedIn | 公開告知と初期反応の収集に向く |

Zenn、Qiita、GitHub Pagesは初回公開後に追加する。初回からすべて作ると、標準本文の確認より配布作業が重くなる。

## 4. 媒体別メッセージ

| 媒体 | 主メッセージ | 避けること |
| --- | --- | --- |
| GitHub | RFP、設計書、監査ログ、RACI、Self-Assessmentへ転記できるPublic Draft標準 | 認証、準拠、安全保証に見せる |
| GitHub Release | v1.0 Public Draftの固定版 | ブランチ上の最新版と混同させる |
| note | AIエージェントには権限、監査、責任、停止権の最低説明項目が必要 | テンプレート一覧だけで終わる |
| X | 公開告知と問題提起 | 誇大表現、断定的な安全保証 |
| LinkedIn | 企業導入、SI、監査、法務に接続できる統治テンプレート | 技術者向け内輪表現 |
| Zenn | RFP、設計書、監査ログへの落とし込み | npm installするOSSのように見せる |
| Qiita | 監査ログ項目、API Agent Context、RACI例 | 統治文書の背景を省略しすぎる |
| GitHub Pages | READMEより読みやすいドキュメントサイト | GitHub正本との版ずれ |

## 5. 公開時の最小セット

初回公開時に最低限必要なもの:

- 公開用GitHub repo
- `README.md`
- `LICENSE.md`
- `docs/release-readiness-v1.0.md`
- `docs/standards/minimum-viable-standard-v1.0.md`
- `docs/templates/`
- `docs/examples/procurement-ai-agent-example.md`
- GitHub Release `v1.0.0-public-draft`
- note記事
- X告知
- LinkedIn告知

## 6. 公開時に強調すること

- Public Draftであり、Final Standardではない
- 認証、準拠、安全保証、法務助言、外部監査、実装ではない
- RFP、設計書、監査ログ、RACI、Self-Assessmentへ転記するための実務テンプレート集である
- 実務で使われた結果をv1.1へ戻す

## 7. 公開後の反応収集

公開後は、以下の反応を集める。

| 反応 | v1.1への反映先 |
| --- | --- |
| RFPに貼るには長い、短い | RFP追補、短縮版 |
| 監査ログ項目が実装しづらい | Audit Log Standard |
| RACIの役割が業務に合わない | AI Agent RACI |
| A2A責任境界が契約へ落ちない | A2A Responsibility Boundary |
| Self-Assessmentが重い | Self-Assessment Checklist |
| Evidence Packageの証跡粒度が曖昧 | Evidence Package |
| 認証と誤解される | README、Release Readiness、LICENSE |
