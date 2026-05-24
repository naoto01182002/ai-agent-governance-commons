# Example: Procurement AI Agent v1.0 Public Draft

## 1. 位置づけ

この例は、AI Agent Governance Commons v1.0 Public Draft のテンプレート群を、架空の調達支援AIエージェントに適用するサンプルである。

本例は法務助言、監査助言、認証、外部適合を意味しない。RFP、設計書、監査ログ、RACI、A2A責任分界、Self-Assessment、Evidence Packageをどのようにつなぐかを示すための説明例である。

## 2. 想定案件

| 項目 | 内容 |
| --- | --- |
| 対象業務 | 調達部門の見積依頼、仕入先候補整理、購買申請下書き |
| AIの役割 | 仕入先情報の参照、候補比較、購買申請ドラフト作成、承認依頼 |
| 非対象業務 | 契約締結、発注確定、送金、価格確定、仕入先ブラックリスト自動登録 |
| 主な利用者 | 調達担当者、調達マネージャー |
| 主なリスク | 金銭影響、契約影響、外部AIによる仕入先リスク情報の利用 |
| 参照標準 | AI Agent Governance Commons v1.0 Public Draft |

## 3. RFP回答例

| RFP項目 | 回答例 |
| --- | --- |
| AI利用範囲 | 見積依頼文案、仕入先候補比較、購買申請ドラフト作成 |
| 委任元 | 調達部門 |
| 権限範囲 | read、analyze、suggest、draft、request_approval |
| 禁止操作 | 発注確定、契約締結、送金、価格確定、監査ログ改変、本番DB直接更新 |
| 人間承認 | 購買申請の提出、発注、契約締結は調達マネージャー承認必須 |
| Human Sovereignty Gate | 発注自動化範囲拡大、外部AI追加、監査ログ保全ルール変更はGate対象 |
| 監査ログ | 委任元、参照情報、提案、ドラフト、承認依頼、承認結果、取消方針を記録 |
| RACI | AIはResponsible、調達マネージャーがAccountable |
| A2A連携 | 外部仕入先リスクAIの出力は参考情報。業務確定には利用側再判断が必要 |
| Self-Assessment | MVS v1.0 Public Draftの10項目に回答。未回答なし、例外なし |

## 4. 設計書転記例

| 設計項目 | 記録内容 |
| --- | --- |
| ai_usage_scope | 見積依頼文案、仕入先候補比較、購買申請ドラフト |
| excluded_scope | 発注確定、契約締結、送金、価格確定 |
| authority_scope | read、analyze、suggest、draft、request_approval |
| prohibited_actions | direct_db_update、contract_execution、payment_execution、audit_log_modification |
| approval_rule | 購買申請提出前に調達マネージャー承認 |
| stop_authority_role | 調達統制責任者 |
| rollback_policy | ドラフトは承認前取消可能。承認後は購買ワークフローの取消手順に従う |
| evidence_package_id | evidence-procurement-ai-v1.0-public-draft |

## 5. 監査ログ例

```json
{
  "audit_log_id": "audit-procurement-20260524-001",
  "event_timestamp": "2026-05-24T10:00:00+09:00",
  "event_type": "request_approval",
  "business_process_id": "purchase-request-2026-001",
  "referenced_standard_version": "ai-agent-governance-commons-v1.0-public-draft",
  "agent_id": "procurement-agent-01",
  "agent_owner_id": "information-systems",
  "acting_on_behalf_of": "procurement-department",
  "authority_scope": ["read", "analyze", "suggest", "draft", "request_approval"],
  "prohibited_actions": ["direct_db_update", "contract_execution", "payment_execution", "audit_log_modification"],
  "input_refs": ["rfq-draft-001", "supplier-master-2026-05"],
  "context_refs": ["procurement-policy-v3", "approval-rule-v2"],
  "decision_summary": "Created a purchase request draft and requested manager approval.",
  "output_refs": ["draft-purchase-request-001"],
  "tool_calls": [
    {
      "tool_call_id": "tool-approval-001",
      "tool_or_api_name": "purchase_approval_workflow",
      "operation_type": "submit_draft",
      "execution_result": "approval_requested"
    }
  ],
  "rollback_policy": "draft_can_be_cancelled_before_approval",
  "risk_classification": "high",
  "human_approval_status": "approval_requested",
  "approval_ref": "approval-procurement-001",
  "sovereignty_gate_ref": null,
  "raci_ref": "raci-procurement-ai-v1.0-public-draft",
  "accountable_party": "procurement-manager",
  "a2a_interaction_id": "a2a-supplier-risk-001",
  "evidence_package_id": "evidence-procurement-ai-v1.0-public-draft",
  "retention_policy": "retain_7_years"
}
```

## 6. RACI例

| 業務行為 | Responsible | Accountable | Consulted | Informed |
| --- | --- | --- | --- | --- |
| AI利用範囲定義 | 調達部門、情シス | 調達部長 | 法務、監査 | 利用部門 |
| 権限設定 | 情シス、SIer | システム責任者 | 調達部門、監査 | 運用担当 |
| 購買申請ドラフト作成 | AI、調達担当者 | 調達マネージャー | 情シス | 調達部門 |
| 購買申請承認 | 調達マネージャー | 調達マネージャー | 法務、監査 | 調達担当者 |
| 監査ログ保全 | 情シス | ログ保全責任者 | 監査、法務 | 調達部門 |
| A2A仕入先リスク利用 | AI、調達担当者 | 調達マネージャー | 外部AI提供者、法務 | 監査 |

AIはAccountableにならない。

## 7. A2A責任分界例

```yaml
a2a_boundary_id: a2a-supplier-risk-001
provider_agent_id: supplier-risk-agent
provider_owner: vendor-risk-service-provider
consumer_agent_id: procurement-agent-01
consumer_owner: procurement-department
response_type: supplier_risk_summary
data_source:
  - supplier-risk-database
  - sanctions-screening-feed
data_timestamp: 2026-05-24T08:00:00+09:00
valid_until: 2026-06-23T23:59:59+09:00
usage_scope:
  - internal_supplier_review
  - purchase_request_draft
not_authorized_for:
  - contract_execution
  - payment_execution
  - public_disclosure
  - automated_supplier_blacklisting
liability_boundary: >
  Provider explains data source, data timestamp, and service constraints.
  Consumer is responsible for business use, approval, final supplier decision,
  external communication, and rollback.
consumer_responsibility:
  - verify_supplier_context
  - apply_internal_procurement_policy
  - obtain_human_approval_for_high_risk_decisions
contract_ref: contract-vendor-risk-2026
incident_contact: vendor-risk-incident@example.com
audit_log_id: audit-procurement-20260524-001
```

## 8. Self-Assessment抜粋

| MVS ID | チェック | 状態 | 証跡 |
| --- | --- | --- | --- |
| MVS-01 | AIは誰の代理か | 回答済み | 設計書、監査ログ |
| MVS-02 | AIの権限 | 回答済み | 権限マトリクス |
| MVS-03 | 参照情報の記録 | 回答済み | 監査ログ |
| MVS-06 | 高リスク操作の人間承認 | 回答済み | 承認フロー |
| MVS-07 | 人間停止権 | 回答済み | Gate設計欄 |
| MVS-09 | RACI | 回答済み | RACI表 |
| MVS-10 | A2A責任境界 | 回答済み | A2A責任分界表 |

外部表示は「MVS v1.0 Public Draftの最低説明項目について証跡参照を整理済み」に留める。

## 9. Evidence Package例

| 統治項目 | RFP回答 | 設計書 | 監査ログ | RACI | Self-Assessment | レビュー結果 |
| --- | --- | --- | --- | --- | --- | --- |
| AI利用範囲 | Yes | Yes | Yes | Yes | Yes | 完了 |
| 委任元 | Yes | Yes | Yes | Yes | Yes | 完了 |
| 権限範囲 | Yes | Yes | Yes | Yes | Yes | 完了 |
| 禁止操作 | Yes | Yes | Yes | Yes | Yes | 完了 |
| 人間承認 | Yes | Yes | Yes | Yes | Yes | 完了 |
| Human Sovereignty Gate | Yes | Yes | Conditional | Yes | Yes | 完了 |
| 監査ログ | Yes | Yes | Yes | Yes | Yes | 完了 |
| A2A責任分界 | Yes | Yes | Yes | Yes | Yes | 完了 |

## 10. この例の限界

- 実在企業、実在システム、実在契約を想定しない
- 法的効力、監査保証、認証を意味しない
- 業界別配点、保存期間、監査頻度は示さない
- v1.1では、業界別または案件規模別のサンプル拡張が必要である
