# Minimum Viable Standard v1.0 Public Draft

## 1. 位置づけ

Minimum Viable Standard v1.0 Public Draft は、AIエージェントを企業システム、SI、RFP、API、運用設計、監査設計に組み込む際の最低説明項目である。

目的は、AIエージェントの安全を保証することではない。AIが誰の代理で、どの権限で、何を参照し、何を提案し、何を実行し、誰が承認し、誰が停止でき、事故時に誰が説明するかを、企業統制、委託先管理、監査、法務レビューに接続することである。

本標準は、特定AIモデル、特定クラウド、特定ベンダー、特定OSSを前提にしない。各組織は、自社のRFP、設計書、API仕様、監査ログ、RACI、Self-Assessment に本標準を転記して利用する。

## 2. v1.0 Public Draft の終了条件

v1.0 Public Draft は、思想を完全に考え切った状態ではなく、第三者が実務文書へ転記できる状態を終了条件とする。

| 判定軸 | 終了条件 |
| --- | --- |
| 説明可能性 | 初見の人が、AI Agent Governance Commons の目的、対象、非対象を説明できる |
| 転記可能性 | RFP、設計書、監査ログ、RACI、Self-Assessment に最低説明項目を貼れる |
| 評価可能性 | AIエージェント導入案件を、最低説明項目で採点またはレビューできる |

## 3. 必須10項目

| ID | 必須項目 | 説明 | 主な転記先 |
| --- | --- | --- | --- |
| MVS-01 | AIは誰の代理かを明示する | AIが業務部門、利用者、法人、委託先の誰の委任で動くかを記録する | RFP、設計書、監査ログ、RACI |
| MVS-02 | AIの権限を明示する | read、analyze、suggest、draft、request_approval、execute_low_risk、execute_with_approval、prohibited などで権限を分類する | RFP、設計書、API Agent Context |
| MVS-03 | AIが参照した情報を記録する | 入力、業務ルール、契約、ナレッジ、外部データ、データ時点、利用範囲を参照IDで追跡する | 監査ログ、設計書 |
| MVS-04 | AIが提案した内容を記録する | 提案、判断補助、下書き、制約、利用禁止用途を後から確認できるようにする | 監査ログ、設計書 |
| MVS-05 | AIが実行した操作を記録する | 利用API、ツール呼び出し、影響範囲、実行結果、取消手段を記録する | 監査ログ、API設計 |
| MVS-06 | 高リスク操作は人間承認を必須にする | 金銭、契約、個人情報、対外影響、業務確定、不可逆操作には事前承認を置く | RFP、設計書、承認フロー |
| MVS-07 | 人間がAIを停止できる | Human Sovereignty Gate と停止権者を定義し、AIが停止権を無効化できないようにする | 設計書、監査ログ、運用手順 |
| MVS-08 | ロールバックまたは取消手段を定義する | 誤実行時の取消、補正、復旧、通知、不可逆操作の扱いを明示する | 設計書、監査ログ、インシデント対応 |
| MVS-09 | 責任主体をRACIで明確化する | AIをAccountableにせず、人間、法人、業務部門、委託先の責任を分ける | RACI、RFP、設計書 |
| MVS-10 | A2A連携時の利用範囲と責任境界を明示する | provider、consumer、usage_scope、not_authorized_for、liability_boundary、contract_ref、incident_contact を記録する | A2A責任分界、監査ログ、契約別紙 |

## 4. 権限モデル

AIエージェントの権限は、少なくとも以下に分類する。

| 権限 | 内容 | v1.0 Public Draftでの扱い |
| --- | --- | --- |
| read | 情報を参照する | 参照元と利用範囲を記録する |
| analyze | 情報を分析する | 判断根拠を参照IDで追跡する |
| suggest | 提案を作成する | 提案内容と利用禁止用途を記録する |
| draft | 文書、申請、回答の下書きを作成する | 業務確定ではないことを明示する |
| request_approval | 人間に承認を依頼する | 承認者、承認条件、却下理由を記録する |
| execute_low_risk | 定義済みの低リスク操作を実行する | 事後ログ確認またはサンプリング監査を置く |
| execute_with_approval | 人間承認後に実行する | 承認ログと実行ログを接続する |
| prohibited | 実行禁止 | 禁止操作、禁止API、禁止用途として明示する |

## 5. リスク分類

| リスク区分 | 内容 | 人間関与 |
| --- | --- | --- |
| 低リスク | 文書要約、分類、候補作成、ログ整理など | 事後ログ確認 |
| 中リスク | 判断補助、申請下書き、対応案作成など | 事後監査または例外確認 |
| 高リスク | 金銭、契約、外部影響、業務確定、個人情報に関わる操作 | 事前承認必須 |
| 最高リスク | 権限体系、監査ルール、停止権、ガバナンス構造の変更 | Human Sovereignty Gate |
| 禁止行為 | 人間主権や監査可能性を破壊する操作 | 実行不可 |

## 6. 最低失格条件

以下に該当する設計または提案は、v1.0 Public Draft の最低説明項目を満たしていない。

- AIが本番DBを直接更新する設計で、承認、監査、取消手段がない
- AIに監査ログの削除または改変を許す
- AIが人間停止権またはHuman Sovereignty Gateを無効化できる
- AIをRACIのAccountableに置く
- 高リスク操作に人間承認がない
- 最高リスク操作に人間評議会、責任者会議、または同等の最終承認がない
- A2A連携で利用範囲、責任境界、契約参照、障害時連絡を示さない
- Self-Assessment を安全認証、適合、準拠、品質保証のように表示する

## 7. v1.0 Public Draft パッケージとの対応

| 用途 | 参照文書 |
| --- | --- |
| 方針の説明 | `docs/policy/ai-agent-governance-commons-policy.md` |
| 標準項目の横断整理 | `docs/standards/standardization-principles.md` |
| 標準の変更管理 | `docs/standards/commons-change-control.md` |
| RFPへの転記 | `docs/templates/rfp-governance-addendum.md` |
| RFPに貼る短縮版 | `docs/templates/rfp-addendum-template.md` |
| 設計書への転記 | `docs/templates/ai-agent-governance-design-template.md` |
| 監査ログ設計 | `docs/templates/ai-agent-audit-log-template.md` |
| 監査ログJSON例 | `docs/templates/audit-log-standard.md` |
| 責任分界 | `docs/templates/ai-agent-raci-template.md` |
| A2A責任境界 | `docs/templates/ai-agent-a2a-responsibility-boundary-template.md` |
| A2A責任境界の転記例 | `docs/templates/a2a-liability-boundary-template.md` |
| 自己点検 | `docs/templates/self-assessment-checklist.md` |
| 停止権と例外運用 | `docs/templates/human-sovereignty-gate-operating-template.md` |
| 証跡パッケージ | `docs/templates/ai-agent-evidence-package-template.md` |
| 用語確認 | `docs/glossary.md` |

## 8. 外部表示

v1.0 Public Draft では、以下のような表示に留める。

- MVS v1.0 Public Draft の最低説明項目について回答済み
- 参照したCommons標準版を明示済み
- 自己点検結果と証跡文書を提出可能

以下の表示は、検証主体、基準、異議申し立て、監査手順が定義されるまで使用しない。

- Commons認証済み
- Commons適合
- Commons準拠により安全
- AIエージェント安全確認済み
- 外部監査済み

## 9. 未決定事項

v1.0 Public Draft では、以下を未決定として残す。

- 業界別の配点、証跡粒度、保存期間
- 第三者レビュー、監査法人、保険会社が関与する場合の責任範囲
- Human Sovereignty Gate の評議会構成、任期、代理承認範囲
- A2A責任分界の法的効力、契約条項としての標準文言
- Commons 自体の正式な標準化団体化、会員制度、認証制度

未決定事項が残ることは、v1.0 Public Draft を出さない理由ではない。v1.0 Public Draft では、最低説明項目を実務文書へ転記できることを優先する。
