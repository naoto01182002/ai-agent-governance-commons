# Commons Change Control v1.0 Public Draft

## 1. 位置づけ

Commons Change Control v1.0 Public Draft は、AI Agent Governance Commons の標準項目を、誰が、どの根拠で、どの状態として扱うかを記録するための最低限の変更管理標準である。

本標準は、外部認証制度、会員制度、投票制度、法的適合制度を定義するものではない。

目的は、AIエージェント統治標準そのものが不透明に変わることを避け、RFP、設計書、監査ログ、RACI、Self-Assessment に転記できる変更履歴と判断根拠を残すことである。

AI Agent Governance Commons は、AIの権限、監査、停止権、責任分界を社会側に残すことを目的とする。そのため、Commons 自体の改訂権限も、説明不能な中央集権や個人判断に寄せてはならない。

## 2. 適用範囲

本標準は、以下の追加、改訂、廃止、状態変更に適用する。

- Minimum Viable Standard v1.0 Public Draft
- AIエージェント権限モデル
- AIリスク分類
- Human-on-the-loop
- Human Sovereignty Gate
- AI監査ログ標準
- AI Agent RACI
- A2A責任分界
- RFP追補テンプレート
- 設計書・運用設計への注入項目
- API Agent Context
- Self-Assessment Checklist
- Commons 自体の用語、版数、状態、外部表示ルール

実装コード、特定ベンダー製品設定、特定AIモデルの機能仕様、特定クラウドの管理画面設計は、本標準の直接対象ではない。

## 3. 標準項目の状態

Commons の標準項目は、初期段階では以下の4状態で扱う。

| 状態 | 意味 | RFP・設計書での扱い |
| --- | --- | --- |
| proposed | 論点として提案された状態 | 必須要求にはしない。検討論点として参照できる |
| draft | 文書またはテンプレート案に反映され、試用できる状態 | 案件リスクに応じて採用可否と例外を明記する |
| recommended | 複数文書に整合的に反映され、初期採用を推奨できる状態 | RFP、設計書、Self-Assessment の標準項目候補にできる |
| deprecated | よりよい項目に置き換えられ、将来削除候補となる状態 | 代替項目、移行期限、旧版維持理由を併記する |

recommended は、安全認証、外部適合、法的準拠を意味しない。

deprecated は、即時無効を意味しない。既存案件では、移行期限、代替項目、旧項目を維持するリスク、監査時の扱いを明記する。

## 4. 変更種別とリスク分類

Commons の変更は、以下の種別で扱う。

| 変更種別 | 例 | 基本リスク |
| --- | --- | --- |
| 用語明確化 | 誤解を避ける説明追加、表現統一 | 低 |
| テンプレート追加 | RFP欄、設計書欄、Self-Assessment項目の追加 | 中 |
| 標準項目追加 | 新しい必須項目、ログ項目、RACI項目の追加 | 中または高 |
| 意味変更 | MVS、権限、リスク分類、RACI、A2A責任分界の意味変更 | 高 |
| 統治変更 | 停止権、責任分界、監査ログ、AIの責任位置づけを変える変更 | 最高 |
| 廃止 | 項目のdeprecated化、代替項目への移行 | 中または高 |

Human Sovereignty Gate、AIをAccountableにしない原則、人間停止権、監査ログ保全、A2A責任分界を弱める変更は、最高リスク変更として扱う。

AIが変更案や影響分析を生成することはあり得る。しかし、AIは標準変更の最終責任主体にはならない。AIはResponsibleまたはConsultedになり得るが、Accountableにはならない。

## 5. 変更提案の必須項目

標準項目の追加、改訂、廃止、状態変更を提案する場合、少なくとも以下を記録する。

- change_proposal_id
- proposed_date
- proposer
- affected_standard_items
- current_status
- proposed_status
- change_type
- risk_classification
- proposal_summary
- reason_for_change
- affected_documents
- affected_stakeholders
- expected_benefit
- operational_burden
- audit_impact
- legal_or_contract_impact
- backward_compatibility
- migration_requirement
- alternative_options
- objections_or_risks
- consequence_if_rejected
- human_approval_required
- sovereignty_gate_required
- decision
- decision_reason
- decision_date
- review_due_date

変更提案は、標準本文だけでなく、RFP、設計書、API Agent Context、監査ログ、RACI、Self-Assessment のどこに影響するかを明示しなければならない。

影響文書を示せない変更は、思想として妥当であっても、企業システムへ注入可能な標準としては保留する。

## 6. 採択判断

proposed から draft へ進めるには、提案理由、対象レイヤー、影響文書、想定ステークホルダー、採択しない場合の不利益が記録されていなければならない。

draft から recommended へ進めるには、少なくとも方針、標準、テンプレート、監査またはRACIのいずれか複数文書で矛盾なく扱えることを確認する。

recommended へ進める判断は、初期段階では単独の思想判断にしない。少なくとも企画、標準化、実務テンプレート、批判の観点を記録し、反対意見または残リスクを併記する。

deprecated へ進める場合は、代替項目、移行期限、旧項目を使い続ける場合のリスク、既存RFP・設計書・監査ログ・契約への影響を記録する。

採択判断は、Commons の安全性を保証するものではない。判断の目的は、採用者がどの根拠で標準項目を使ったかを後から説明できるようにすることである。

## 7. 最低失格条件

以下に該当する変更提案は、原則として採択しない。

- AIをRACIのAccountableに置く
- AIが人間停止権を無効化できる設計にする
- AIに監査ログの削除または改変を許す
- 本番DB直接更新を、承認、監査、取消手段なしに認める
- 高リスク操作から人間承認を外す
- A2A連携で利用範囲と責任境界を不要にする
- 特定AIモデル、特定クラウド、特定ベンダー、特定OSSを前提にする
- RFP、設計書、監査ログ、RACI、Self-Assessment への影響を説明しない
- 標準を重くしすぎ、現実的な企業導入を阻害する
- 標準を軽くしすぎ、説明責任や監査可能性を失わせる

最低失格条件は、外部認証の不合格基準ではない。Commons 自体が中核原則に反する変更を採択しないための内部統制である。

## 8. Human Sovereignty Gate との関係

Commons の標準変更であっても、以下に該当する場合は Human Sovereignty Gate 相当の扱いを必要とする。

- 人間停止権の対象、権限、独立性を弱める
- AI Agent RACI における最終責任主体を曖昧にする
- 監査ログの保全、改ざん防止、復元可能性を弱める
- 高リスクまたは最高リスク操作の人間承認を減らす
- A2A責任分界の利用範囲、責任境界、契約参照、障害時連絡を弱める
- MVS v1.0 Public Draft を安全認証または外部適合のように見せる

Human Sovereignty Gate 相当の変更では、停止権者、承認者、利益相反確認、却下理由、再提案条件、監査ログ参照を記録する。

停止は永久否決に限定しない。期限付き凍結、条件付き再提案、追加証跡要求として扱える。ただし、AIが停止判断を上書きする経路を持ってはならない。

## 9. バージョンと互換性

Commons の文書、テンプレート、Self-Assessment には、参照した標準版と評価日を残す。

RFPでは、発注者が参照する Commons の版、参照日、採用項目、例外、契約後改訂時の扱いを明記できることが望ましい。

契約後に標準が改訂された場合の扱いは、即時反映、次回更改時反映、影響分析後に反映、適用除外のいずれかとして案件ごとに定義する。

破壊的変更は、既存RFP、設計書、監査ログ、RACI、委託先管理、契約別紙に影響するため、通常の文言修正とは分けて扱う。

Self-Assessment の結果に標準版がない場合、後から何を説明済みとしたのか復元できないため、監査・法務レビュー上の価値が下がる。

## 10. 実務文書への注入項目

RFP追補には、以下を追加候補とする。

- referenced_standard_version
- referenced_date
- applied_standard_items
- item_status
- exception_reason
- evidence_documents
- design_document_mapping
- audit_log_mapping
- raci_mapping
- post_contract_change_policy

設計書には、以下を追加候補とする。

- standard_item_id
- standard_version
- item_status
- applied_scope
- exception_reason
- migration_required
- review_date
- related_raci_ref
- related_audit_log_ref

監査ログには、以下を追加候補とする。

- standard_version
- template_version
- self_assessment_ref
- change_proposal_ref
- exception_approval_ref
- human_approval_ref
- sovereignty_gate_ref
- migration_status

Self-Assessment には、以下を追加候補とする。

- assessed_standard_version
- assessment_date
- assessment_owner
- unanswered_items
- exception_approval
- next_review_date
- reassessment_trigger
- external_statement

## 11. 外部表示の制限

MVS v1.0 Public Draft と Commons Change Control v1.0 Public Draft は、安全認証、外部適合、法的準拠、品質保証を意味しない。

外部向けに自己点検結果を表示する場合、初期段階では以下のような表現に限定する。

- MVS v1.0 Public Draft の最低説明項目について回答済み
- Commons の参照標準版を明示済み
- 自己点検結果と証跡文書を提出可能

以下の表現は、検証主体、基準、異議申し立て、監査手順が定義されるまで使用しない。

- Commons認証済み
- Commons適合
- Commons準拠により安全
- AIエージェント安全確認済み
- 外部監査済み

外部表示の目的は、採用者が説明した範囲を明確にすることであり、安全性を保証するラベルを作ることではない。

## 12. 未決定事項

以下は v1.0 Public Draft では未決定として残す。

- recommended への状態遷移を誰が最終承認するか
- 反対意見や異議申し立てをどの公開単位で扱うか
- 第三者レビューを導入する場合の主体、基準、責任
- Self-Assessment の外部表示に添付すべき証跡範囲
- deprecated 項目の標準移行期限
- 契約条項、委託先管理、法務レビューとの標準接続文言
- Commons 自体の正式な運営体制、会員制度、投票制度の要否

これらは、標準本文を増やす前に継続して検討すべき統治論点である。
