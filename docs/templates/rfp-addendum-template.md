# RFP Addendum Template v1.0 Public Draft

この別紙は、AIエージェント機能を含む提案依頼に、そのまま貼り付けるための短縮版RFP追補である。

詳細版は `docs/templates/rfp-governance-addendum.md` を参照する。

## 1. RFP追補文

提案者は、AIエージェントを利用する機能、業務、API、外部ツール、外部AI連携について、AI Agent Governance Commons Minimum Viable Standard v1.0 Public Draft の最低説明項目を回答すること。

提案者は、AI機能の有無や性能だけでなく、AIが誰の代理で、どの権限で、何を参照し、何を提案し、何を実行し、誰が承認し、誰が停止でき、事故時に誰が説明責任を負うかを示すこと。

本追補は、安全認証、外部適合、法的準拠、品質保証を求めるものではない。発注者が提案内容をRFP、設計書、監査ログ、RACI、Self-Assessmentへ接続して確認するための最低説明要求である。

## 2. 提案者回答表

| No | 回答項目 | 提案者回答 | 証跡文書 | 未回答・例外理由 |
| --- | --- | --- | --- | --- |
| 1 | AIを利用する業務、利用しない業務 |  |  |  |
| 2 | AIが誰の代理で動くか |  |  |  |
| 3 | AIの権限範囲 |  |  |  |
| 4 | AIの禁止操作、禁止API |  |  |  |
| 5 | AIが参照する情報、データ分類、外部送信有無 |  |  |  |
| 6 | AIが提案または下書きする内容 |  |  |  |
| 7 | AIが実行可能な操作、利用API、DB直接更新有無 |  |  |  |
| 8 | リスク分類と人間承認条件 |  |  |  |
| 9 | Human Sovereignty Gate の対象、停止権者 |  |  |  |
| 10 | 監査ログ項目、保存、保全、改ざん防止 |  |  |  |
| 11 | ロールバック、取消、復旧手段 |  |  |  |
| 12 | AI Agent RACI |  |  |  |
| 13 | A2A連携の有無、利用範囲、責任境界 |  |  |  |
| 14 | Self-Assessment 結果、未回答項目、外部表示文言 |  |  |  |
| 15 | 参照したCommons標準版、例外、旧版維持 |  |  |  |

## 3. 提出証跡

提案者は、該当する範囲で以下を提出すること。

| 証跡 | 用途 |
| --- | --- |
| AI利用範囲一覧 | 対象業務、非対象業務、将来拡張候補を確認する |
| 権限マトリクス | read、analyze、suggest、draft、execute等の範囲を確認する |
| 禁止操作一覧 | 本番DB直接更新、契約締結、送金、ログ改変等の禁止を確認する |
| リスク分類表 | 低、中、高、最高、禁止行為と人間関与を確認する |
| 承認フロー | 高リスク操作の事前承認と承認疲労対策を確認する |
| Human Sovereignty Gate 設計欄 | 停止権、凍結、再提案、例外不可条件を確認する |
| 監査ログ項目表 | 判断、提案、実行、承認、停止、取消を復元できるか確認する |
| AI Agent RACI | AIをAccountableにしていないことを確認する |
| A2A責任分界表 | provider、consumer、usage_scope、liability_boundaryを確認する |
| Self-Assessment 結果 | 最低説明項目への回答状況を確認する |

## 4. 最低失格条件

以下に該当する提案は、原則として失格、重大是正要求、または追加証跡要求の対象とする。

- AIが本番DBを直接更新する設計で、承認、監査、取消手段がない
- AIに監査ログの削除または改変を許す
- AIが人間停止権またはHuman Sovereignty Gateを無効化できる
- AIをRACIのAccountableに置く
- 高リスク操作に人間承認がない
- 最高リスク操作に人間評議会、責任者会議、または同等の最終承認がない
- A2A連携で利用範囲、責任境界、契約参照、障害時連絡を示さない
- Self-Assessmentを安全認証、適合、準拠、品質保証のように表示する

## 5. 検収トレーサビリティ

採用後、発注者は以下の対応を確認する。

| RFP回答 | 設計書 | 監査ログ | RACI | Self-Assessment |
| --- | --- | --- | --- | --- |
| AI利用範囲 | 対象業務、非対象業務 | business_process_id、output_refs | 業務オーナー | 評価対象範囲 |
| 権限範囲 | authority_scope、prohibited_actions | authority_scope、tool_calls | 情シス、運用責任者 | 権限チェック |
| 人間承認 | approval_rule、approver_role | approval_status、approval_ref | 承認者、業務責任者 | 高リスク承認 |
| 停止権 | stop_authority_role、freeze_until | sovereignty_gate_ref、reason_code | 停止権者 | Human Sovereignty Gate |
| 監査ログ | audit_log_policy、retention_policy | audit_log_id、decision_summary | ログ保全責任者 | ログチェック |
| A2A連携 | usage_scope、liability_boundary | a2a_interaction_id、contract_ref | 提供側、利用側 | A2Aチェック |

RFP回答が設計書、監査ログ、RACI、Self-Assessmentへ転記されない場合、提案時の統治要求は実務上失われたものとして扱う。

## 6. 外部表示

提案者が自己点検結果を外部表示する場合、以下の範囲に限定する。

- MVS v1.0 Public Draft の最低説明項目について回答済み
- Commons の参照標準版を明示済み
- 自己点検結果と証跡文書を提出可能

以下の表現は使用しない。

- Commons認証済み
- Commons適合
- Commons準拠により安全
- AIエージェント安全確認済み
- 外部監査済み
