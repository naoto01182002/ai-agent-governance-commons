# AI Agent Governance Commons

AI Agent Governance Commons は、AIエージェントを企業システム、SI、RFP、API、運用設計、監査設計に組み込む際の公共ドラフト標準と実務テンプレート集です。

| Field | Value |
| --- | --- |
| Version | v1.0 Public Draft |
| Status | Initial public release |
| Scope | Minimum governance standard and practical templates |
| Not | certification, compliance, legal advice, safety guarantee, external audit, or product implementation |

AIが誰の代理で、どの権限を持ち、何を参照し、何を提案し、何を実行し、誰が承認し、誰が停止でき、誰が説明責任を負うのかを、RFP、設計書、監査ログ、RACI、Self-Assessment へ転記できる形で整理します。

特定AIモデル、特定クラウド、特定ベンダー、特定OSSの仕様ではありません。目的は、AI活用を止めることではなく、AIエージェントを企業活動へ入れるときに最低限説明すべき権限、監査、責任、停止権、人間関与、A2A責任分界を、第三者が実務文書へ転記できる形で提供することです。

## 基本思想

モデルは借りてもよい。

しかし、業務文脈・権限・監査ログ・停止権・責任分界は社会側に残す。

AIを使う社会ではなく、AIに権力を集中させない社会を設計する。

## v1.0 Public Draft のゴール

AI Agent Governance Commons v1.0 Public Draft のゴールは、思想を完成させることではありません。

AIエージェント導入時に、RFP、設計書、監査ログ、RACI、Self-Assessment へ転記できる最低限の公共標準を作ることです。

v1.0 Public Draft は次の3条件を満たした時点で一区切りとします。

| 判定軸 | 終了条件 |
| --- | --- |
| 説明可能性 | 初見の人が3分で構想の目的、対象、非対象を説明できる |
| 転記可能性 | RFP、設計書、監査チェックリスト、RACIにそのまま貼れる |
| 評価可能性 | AIエージェント導入案件を最低説明項目でレビューできる |

## v1.0 Public Draft パッケージ

| 成果物 | ファイル | 使いどころ |
| --- | --- | --- |
| 方針書 | [docs/policy/ai-agent-governance-commons-policy.md](docs/policy/ai-agent-governance-commons-policy.md) | 構想の目的、対象、非対象を説明する |
| Minimum Viable Standard | [docs/standards/minimum-viable-standard-v1.0.md](docs/standards/minimum-viable-standard-v1.0.md) | 最低説明10項目をRFP、設計書、監査に転記する |
| 標準化方針 | [docs/standards/standardization-principles.md](docs/standards/standardization-principles.md) | 権限、リスク、監査、RACI、A2Aを横断整理する |
| Change Control | [docs/standards/commons-change-control.md](docs/standards/commons-change-control.md) | 標準項目の追加、改訂、廃止、状態変更を管理する |
| RFP追補 | [docs/templates/rfp-governance-addendum.md](docs/templates/rfp-governance-addendum.md) | AIエージェントを含む提案でベンダーに回答させる |
| RFP追補別紙 | [docs/templates/rfp-addendum-template.md](docs/templates/rfp-addendum-template.md) | RFPへそのまま貼る短縮版 |
| 設計書テンプレート | [docs/templates/ai-agent-governance-design-template.md](docs/templates/ai-agent-governance-design-template.md) | 要件定義、基本設計、運用設計へ統治項目を転記する |
| 監査ログ項目表 | [docs/templates/ai-agent-audit-log-template.md](docs/templates/ai-agent-audit-log-template.md) | 誰の代理で何を参照、提案、実行、承認したかを復元する |
| 監査ログ標準 | [docs/templates/audit-log-standard.md](docs/templates/audit-log-standard.md) | 必須ログ項目とJSON例を実装・監査に渡す |
| AI Agent RACI | [docs/templates/ai-agent-raci-template.md](docs/templates/ai-agent-raci-template.md) | AIをAccountableにしない責任分界を定義する |
| A2A責任分界 | [docs/templates/ai-agent-a2a-responsibility-boundary-template.md](docs/templates/ai-agent-a2a-responsibility-boundary-template.md) | 他社AI、委託先AI、外部AIとの責任境界を記録する |
| A2A責任境界別紙 | [docs/templates/a2a-liability-boundary-template.md](docs/templates/a2a-liability-boundary-template.md) | A2A責任境界をメッセージ・契約別紙へ転記する |
| Self-Assessment | [docs/templates/self-assessment-checklist.md](docs/templates/self-assessment-checklist.md) | 情シス、監査、法務が導入前に自己点検する |
| Human Sovereignty Gate | [docs/templates/human-sovereignty-gate-operating-template.md](docs/templates/human-sovereignty-gate-operating-template.md) | 停止権、凍結、再提案、例外不可条件を運用する |
| Evidence Package | [docs/templates/ai-agent-evidence-package-template.md](docs/templates/ai-agent-evidence-package-template.md) | RFP、設計書、監査ログ、RACI、Self-Assessmentの証跡を束ねる |
| 用語集 | [docs/glossary.md](docs/glossary.md) | 主要概念の解釈ブレを減らす |
| ロードマップ | [docs/roadmap.md](docs/roadmap.md) | v1.0 Public Draft、v1.1、v2.0の区切りを管理する |
| 公開計画 | [docs/publication/public-launch-plan-v1.0.md](docs/publication/public-launch-plan-v1.0.md) | GitHub、note、X、LinkedIn、後続媒体の役割を分ける |
| Decision Log | [docs/decision-log.md](docs/decision-log.md) | 重要判断への公開入口 |

## 読者別の使い方

| 読者 | まず読むもの | 次に使うもの |
| --- | --- | --- |
| 発注者、調達担当 | [RFP追補別紙](docs/templates/rfp-addendum-template.md) | [Evidence Package](docs/templates/ai-agent-evidence-package-template.md)、[Release Readiness](docs/release-readiness-v1.0.md) |
| SIer、提案者 | [MVS v1.0 Public Draft](docs/standards/minimum-viable-standard-v1.0.md) | [RFP追補詳細版](docs/templates/rfp-governance-addendum.md)、[設計書テンプレート](docs/templates/ai-agent-governance-design-template.md) |
| 情シス、アーキテクト | [標準化方針](docs/standards/standardization-principles.md) | [監査ログ標準](docs/templates/audit-log-standard.md)、[Human Sovereignty Gate](docs/templates/human-sovereignty-gate-operating-template.md) |
| 監査、法務 | [Self-Assessment](docs/templates/self-assessment-checklist.md) | [AI Agent RACI](docs/templates/ai-agent-raci-template.md)、[A2A責任境界別紙](docs/templates/a2a-liability-boundary-template.md) |
| 初めて試す人 | [サンプル案件](docs/examples/procurement-ai-agent-example.md) | [用語集](docs/glossary.md)、[ロードマップ](docs/roadmap.md) |

## リリース状態

v1.0 Public Draft の公開可否と対象文書は [Release Readiness v1.0 Public Draft](docs/release-readiness-v1.0.md) で確認します。

このリポジトリの文書とテンプレートは、特に記載がない限り CC BY 4.0 で利用できます。スクリプトは MIT License です。詳細は [LICENSE.md](LICENSE.md) を参照してください。

この標準を参照したことは、認証、適合、準拠、安全保証、外部監査済みを意味しません。

## Minimum Viable Standard v1.0 Public Draft

AIエージェント導入時の最低説明項目は次の10項目です。

1. AIは誰の代理かを明示する
2. AIの権限を明示する
3. AIが参照した情報を記録する
4. AIが提案した内容を記録する
5. AIが実行した操作を記録する
6. 高リスク操作は人間承認を必須にする
7. 人間がAIを停止できる
8. ロールバックまたは取消手段を定義する
9. 責任主体をRACIで明確化する
10. 他エージェントと連携する場合、利用範囲と責任境界を明示する

この10項目は、安全認証や外部適合を意味しません。「この10項目を説明できないAIエージェント導入は、企業統制、委託先管理、監査、法務レビューに接続できていない」という最低限の説明要求です。

## 目指すもの

- 公開標準として誰でも参照、改善できること
- RFP追補として調達に入りやすいこと
- 設計チェックリストとしてSI、情シスが使いやすいこと
- 監査ログ標準として監査、法務に接続しやすいこと
- RACIテンプレートとして責任分界を明確にできること
- Self-Assessmentとして導入前レビューに使えること

## 最初に目指さないもの

- 認証ビジネス
- OSS実装
- AIエージェント基盤そのもの
- 全業界対応の完全標準
- 法的に厳密な規格

## 公開とフィードバック

公開版は、[公開用manifest](docs/publication/public-repository-manifest.md) に示す docs-only 構成を正本として扱います。作業用private repoをそのままpublic化せず、標準本文、テンプレート、サンプル、公開告知に必要な文書だけを公開用repoへコピーします。

GitHub Release 文、note記事草案、X告知文、LinkedIn告知文、Zenn/Qiita/GitHub Pagesの後続計画は [docs/publication/](docs/publication/) に置いています。

初回公開では、GitHubを正本、noteを背景説明、XとLinkedInを告知入口として扱います。Zenn、Qiita、GitHub Pagesは、初回反応を見た後の後続導線です。公開後は、完全性の追求ではなく、RFP、設計書、監査ログ、RACI、Self-Assessmentへ実際に貼ったときの不足をIssueまたはPull Requestで集め、v1.1で補正します。
