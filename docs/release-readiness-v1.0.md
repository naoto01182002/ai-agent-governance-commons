# Release Readiness v1.0 Public Draft

## 1. 判定

AI Agent Governance Commons v1.0 Public Draft は、Initial public release として公開可能な段階にある。

本判定では、v1.0 Public Draft を安全認証、外部適合、法的準拠、品質保証としては扱わない。v1.0 Public Draft は、AIエージェント導入時に最低限説明すべき権限、監査、責任、停止権、人間関与、A2A責任分界を、RFP、設計書、監査ログ、RACI、Self-Assessmentへ転記できる標準パッケージとして扱う。

| 判定軸 | 状態 | 判定 |
| --- | --- | --- |
| 説明可能性 | README、方針書、MVS、用語集が揃っている | Ready |
| 転記可能性 | RFP、設計書、監査ログ、RACI、A2A、Self-Assessment、Evidence Packageが揃っている | Ready |
| 評価可能性 | 最低失格条件、Self-Assessment、Evidence Package、Release Readinessがある | Ready |
| 配布可能性 | README導線、利用条件、サンプル案件がある | Ready with caveats |
| 外部保証 | 第三者レビュー、認証、適合審査は未定義 | Not in scope |

## 2. v1.0 Public Draft 対象文書

| 区分 | 文書 | v1.0 Public Draft状態 | 用途 |
| --- | --- | --- | --- |
| 入口 | `README.md` | recommended | 初見の利用者向け入口 |
| 方針 | `docs/policy/ai-agent-governance-commons-policy.md` | recommended | 構想の目的、対象、非対象 |
| 標準 | `docs/standards/minimum-viable-standard-v1.0.md` | recommended | 最低説明10項目の正本 |
| 標準 | `docs/standards/standardization-principles.md` | recommended | 権限、リスク、監査、RACI、A2Aの横断整理 |
| 標準 | `docs/standards/commons-change-control.md` | draft | Commons自体の変更管理 |
| RFP | `docs/templates/rfp-addendum-template.md` | recommended | RFPに貼る短縮版 |
| RFP | `docs/templates/rfp-governance-addendum.md` | recommended | RFP追補の詳細版 |
| 設計 | `docs/templates/ai-agent-governance-design-template.md` | recommended | 設計書への転記 |
| 監査 | `docs/templates/audit-log-standard.md` | recommended | 必須ログ項目、JSON例、Schema候補 |
| 監査 | `docs/templates/ai-agent-audit-log-template.md` | recommended | 監査ログ設計の詳細版 |
| 責任分界 | `docs/templates/ai-agent-raci-template.md` | recommended | AIをAccountableにしないRACI |
| A2A | `docs/templates/a2a-liability-boundary-template.md` | recommended | A2A責任境界の短縮版 |
| A2A | `docs/templates/ai-agent-a2a-responsibility-boundary-template.md` | recommended | A2A責任分界の詳細版 |
| 停止権 | `docs/templates/human-sovereignty-gate-operating-template.md` | recommended | Gate運用、停止、凍結、再提案 |
| 自己点検 | `docs/templates/self-assessment-checklist.md` | recommended | 導入前自己点検 |
| 証跡 | `docs/templates/ai-agent-evidence-package-template.md` | recommended | RFP、設計、監査、RACI、Self-Assessmentの証跡索引 |
| 例 | `docs/examples/procurement-ai-agent-example.md` | draft | 架空案件での利用例 |
| 用語 | `docs/glossary.md` | recommended | 用語の横断定義 |
| 計画 | `docs/roadmap.md` | recommended | v1.1以降の扱い |
| 判断 | `docs/decision-log.md` | recommended | 重要判断への公開入口 |
| 利用条件 | `LICENSE.md` | recommended | 利用条件と免責 |
| 公開準備 | `docs/publication/public-repository-manifest.md` | recommended | docs-only公開repoに含める対象 |
| 公開準備 | `docs/publication/public-launch-plan-v1.0.md` | recommended | GitHub、note、X、LinkedIn、後続媒体の役割分担 |
| 公開準備 | `docs/publication/github-release-v1.0-public-draft.md` | draft | GitHub Release本文の草案 |
| 公開準備 | `docs/publication/note-announcement-draft-v1.0.md` | draft | note告知記事の草案 |
| 公開準備 | `docs/publication/x-announcement-draft-v1.0.md` | draft | X告知文の草案 |
| 公開準備 | `docs/publication/linkedin-announcement-draft-v1.0.md` | draft | LinkedIn告知文の草案 |
| 公開準備 | `docs/publication/technical-media-followup-plan-v1.0.md` | draft | Zenn、Qiita、GitHub Pagesの後続展開 |

## 3. 公開前チェック

| チェック | 状態 | 備考 |
| --- | --- | --- |
| READMEがMarkdownとして崩れていない | Done | 外向け入口として修正済み |
| MVS v1.0 Public Draftが独立文書化されている | Done | `minimum-viable-standard-v1.0.md` |
| RFP追補がコピペ可能である | Done | 短縮版と詳細版を分離 |
| Self-Assessmentが独立している | Done | 回答状態、重大未解消条件、外部表示制限あり |
| 監査ログ標準にJSON例がある | Done | Schema候補あり |
| RACIが独立している | Done | AIをAccountableにしない |
| A2A責任分界が独立している | Done | YAML例と契約別紙転記例あり |
| Evidence Packageで文書間を束ねられる | Done | 5/24に追加 |
| 利用条件がある | Done | `LICENSE.md` |
| サンプル案件がある | Done | 調達AIエージェント例を追加 |
| 公開用docs-only manifestがある | Done | `docs/publication/public-repository-manifest.md` |
| GitHub Release本文の草案がある | Done | `docs/publication/github-release-v1.0-public-draft.md` |
| note、X、LinkedIn告知草案がある | Done | `docs/publication/` |
| Zenn、Qiita、GitHub Pagesの後続計画がある | Done | `docs/publication/technical-media-followup-plan-v1.0.md` |

## 4. v1.0 Public Draft で明示的に対象外とすること

- Commons認証、適合、準拠、安全保証
- 第三者審査、監査法人レビュー、保険会社審査
- 法的に厳密な契約条項
- 業界別配点、保存期間、証跡粒度の数値基準
- OSS実装、AIエージェント基盤、特定モデルや特定クラウドの仕様化

## 5. リリース時の表示文言

使ってよい表現:

- AI Agent Governance Commons v1.0 Public Draft を参照
- MVS v1.0 Public Draft の最低説明項目について回答済み
- RFP、設計書、監査ログ、RACI、Self-Assessmentへの証跡参照を整理済み
- 参照した標準版と対象範囲を明示済み

使わない表現:

- Commons認証済み
- Commons適合
- Commons準拠により安全
- AIエージェント安全確認済み
- 外部監査済み

## 6. v1.1へ送る課題

- 業界別または案件規模別のRFP配点例
- Evidence Packageの証跡粒度を、軽量、標準、高リスクでさらに具体化する
- 契約別紙、委託先管理台帳、監査調書への標準接続文言
- Human Sovereignty Gateの評議会構成、代理承認範囲、承認疲労指標
- A2A責任分界の法的効力、複数段A2Aの責任連鎖
- Word、CSV、Excel、JSON Schemaファイルとしての配布形式

## 7. 最終判断

v1.0 Public Draft は、公開可能な最小標準パッケージとして扱える。

ただし、v1.0 Public Draftは完成規格ではない。実務で使われた結果、RFP、設計書、監査ログ、RACI、Self-Assessment、Evidence Packageに不足が見つかった場合、v1.1で補正する。
