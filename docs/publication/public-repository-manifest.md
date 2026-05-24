# Public Repository Manifest v1.0 Public Draft

## 1. 目的

公開用リポジトリは、AI Agent Governance Commons v1.0 Public Draft を第三者が参照、転記、改善できる docs-only パッケージとして見せるために作る。

作業用リポジトリをそのまま public 化しない。公開用リポジトリには、標準本文、テンプレート、サンプル、利用条件、公開告知に必要な文書だけを含める。

## 2. 推奨リポジトリ名

第一候補:

```text
ai-agent-governance-commons
```

代替:

```text
AI-Agent-Governance-Commons
```

## 3. 公開対象

| パス | 扱い | 理由 |
| --- | --- | --- |
| `README.md` | include | 公開入口 |
| `LICENSE.md` | include | 利用条件と非認証表示 |
| `docs/release-readiness-v1.0.md` | include | 公開可否、対象、対象外、表示文言 |
| `docs/glossary.md` | include | 用語定義 |
| `docs/roadmap.md` | include | v1.1以降の扱い |
| `docs/policy/` | include | 構想、対象、非対象 |
| `docs/standards/` | include | MVS、標準化方針、変更管理 |
| `docs/templates/` | include | RFP、設計書、監査ログ、RACI、A2A、Self-Assessment、Evidence Package |
| `docs/examples/` | include | 架空案件での利用例 |
| `docs/publication/` | include | 公開計画、GitHub Release、note、X、LinkedIn告知草案、後続媒体計画 |
| `docs/decision-log.md` | optional | 重要判断の公開入口として含めてもよい |

## 4. 公開対象外

| パス | 扱い | 理由 |
| --- | --- | --- |
| `.env.local` | exclude | 秘密情報を含む可能性がある |
| `.env*` | exclude | サンプル以外は公開対象外 |
| `.agents/` | exclude | 作業用エージェント設定 |
| `AGENTS.md` | exclude | 内部作業指示とmemory contextを含む可能性がある |
| `scripts/` | exclude by default | 日次運用やNotion連携は公開標準本体ではない |
| `docs/reports/` | exclude by default | 日次作業ログであり、標準パッケージ本体ではない |
| `docs/strategy/` | exclude by default | 内部検討ログを含む |
| `.git/` | exclude | 作業履歴を公開しない |
| `.github/` | optional | 公開repo側で必要になった場合だけ作る |

## 5. 公開前チェック

| チェック | 必須 |
| --- | --- |
| `rg --files -g ".env*"` で秘密情報ファイルを確認する | yes |
| `rg "TOKEN|SECRET|PASSWORD|API_KEY|PRIVATE KEY|github_pat|ghp_"` で公開対象を検索する | yes |
| README内に認証、適合、準拠、安全保証ではない旨がある | yes |
| Release Readinessで対象文書と対象外が確認できる | yes |
| `v1.0 Public Draft` 表記が公開対象内で統一されている | yes |
| GitHub Release本文に `Public Draft` と `not certification` がある | yes |

## 6. 初回公開手順案

1. 公開用リポジトリ `ai-agent-governance-commons` を作成する
2. このmanifestのinclude対象だけをコピーする
3. 公開対象内に秘密情報、内部作業指示、日次実行ログがないことを確認する
4. `v1.0.0-public-draft` タグを作る
5. `docs/publication/github-release-v1.0-public-draft.md` をもとにGitHub Releaseを作る
6. note、X、LinkedInで、認証ではなくPublic Draftであることを明記して告知する
7. 反応を見てZenn、Qiita、GitHub Pagesへ展開する

## 7. 表示ルール

使ってよい表現:

- AI Agent Governance Commons v1.0 Public Draft を参照
- MVS v1.0 Public Draft の最低説明項目について回答済み
- RFP、設計書、監査ログ、RACI、Self-Assessmentへの証跡参照を整理済み

使わない表現:

- Commons認証済み
- Commons適合
- Commons準拠により安全
- AIエージェント安全確認済み
- 外部監査済み

## 8. 公開チャネル

| チャネル | 役割 | 優先度 |
| --- | --- | --- |
| GitHub Public Repo | 正本、標準文書、テンプレート配布 | 必須 |
| GitHub Releases | バージョン固定 | 必須 |
| note | 背景、思想、問題提起 | 必須 |
| X | 公開告知、初期反応 | 必須 |
| LinkedIn | 企業、SIer、情シス、監査、法務向け告知 | 推奨 |
| Zenn | 技術者、SIer向け実務解説 | 後続 |
| Qiita | 実装、業務システム寄りの解説 | 後続 |
| GitHub Pages | 読みやすいWeb版 | 後続 |

初回公開の中心は、GitHub Public Repo、GitHub Release、note、X、LinkedInとする。Zenn、Qiita、GitHub Pagesは、初回反応を見てから追加する。
