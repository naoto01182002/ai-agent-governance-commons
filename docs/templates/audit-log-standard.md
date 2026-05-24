# Audit Log Standard v1.0 Public Draft

この文書は、AIエージェント監査ログの必須項目、設計項目表、JSON例をまとめた配布用標準である。

詳細版は `docs/templates/ai-agent-audit-log-template.md` を参照する。

## 1. 目的

監査ログは、AIの内部思考をすべて保存するものではない。

目的は、AIが誰の代理で、どの権限で、何を参照し、何を提案し、何を実行し、誰が承認し、誰が停止できたかを、監査、法務、情シス、業務部門、SIerが後から確認できるようにすることである。

## 2. 必須ログ項目

| 区分 | 項目 | 必須 | 内容 |
| --- | --- | --- | --- |
| 共通 | audit_log_id | Yes | 監査ログID |
| 共通 | event_timestamp | Yes | 発生日時、タイムゾーン |
| 共通 | event_type | Yes | read、analyze、suggest、draft、request_approval、execute、stop、rollback等 |
| 共通 | business_process_id | Yes | 案件、申請、取引、チケット等の業務ID |
| 標準 | referenced_standard_version | Yes | 参照したCommons標準版 |
| 主体 | agent_id | Yes | AIエージェントID |
| 主体 | agent_owner_id | Yes | AI管理主体 |
| 主体 | acting_on_behalf_of | Yes | 委任元、業務オーナー、利用部門 |
| 権限 | authority_scope | Yes | AIに許可された権限 |
| 権限 | prohibited_actions | Yes | 禁止操作、禁止API |
| 参照 | input_refs | Yes | 入力、申請、問い合わせ、文書の参照ID |
| 参照 | context_refs | Recommended | 業務ルール、契約、規程、ナレッジの参照ID |
| 参照 | data_classification | Recommended | 個人情報、機密、公開、契約制限等 |
| 提案 | decision_summary | Yes | AIの判断補助、分類、推奨、提案の概要 |
| 提案 | output_refs | Yes | 生成文書、下書き、処理結果の参照ID |
| 実行 | tool_calls | Conditional | ツールまたはAPI呼び出し |
| 実行 | affected_records_ref | Conditional | 影響を受けた業務データ |
| 実行 | rollback_policy | Yes | 取消、補正、復旧条件 |
| 承認 | risk_classification | Yes | 低、中、高、最高、禁止行為 |
| 承認 | human_approval_status | Yes | 不要、承認済み、却下、差し戻し、例外承認等 |
| 承認 | approval_ref | Conditional | 承認ログ参照 |
| 停止 | sovereignty_gate_ref | Conditional | Human Sovereignty Gate判断参照 |
| RACI | raci_ref | Yes | 対応するRACI表 |
| RACI | accountable_party | Yes | 最終責任主体。AI不可 |
| A2A | a2a_interaction_id | Conditional | A2A連携ID |
| 保全 | retention_policy | Yes | 保存期間、保全責任 |
| 保全 | integrity_control | Recommended | 改ざん検知、変更履歴、削除防止 |

Conditional は、該当する行為や連携がある場合に必須とする。

## 3. JSON例

```json
{
  "audit_log_id": "audit-20260523-0001",
  "event_timestamp": "2026-05-23T09:30:00+09:00",
  "event_type": "execute",
  "business_process_id": "purchase-request-12345",
  "referenced_standard_version": "ai-agent-governance-commons-v1.0-public-draft",
  "agent_id": "agent-procurement-01",
  "agent_owner_id": "information-systems",
  "acting_on_behalf_of": "procurement-department",
  "authority_scope": ["read", "analyze", "draft", "request_approval"],
  "prohibited_actions": ["direct_db_update", "contract_execution", "payment_execution", "audit_log_modification"],
  "input_refs": ["rfq-2026-001", "supplier-master-ref"],
  "context_refs": ["procurement-policy-v3", "approval-rule-v2"],
  "data_classification": "confidential",
  "decision_summary": "Generated a purchase request draft and requested human approval.",
  "output_refs": ["draft-pr-12345"],
  "tool_calls": [
    {
      "tool_call_id": "tool-001",
      "tool_or_api_name": "purchase_request_api",
      "operation_type": "submit_draft",
      "execution_result": "approval_requested"
    }
  ],
  "affected_records_ref": ["purchase-request-12345"],
  "rollback_policy": "draft_can_be_cancelled_before_human_approval",
  "risk_classification": "high",
  "human_approval_status": "approval_requested",
  "approval_ref": "approval-req-12345",
  "sovereignty_gate_ref": null,
  "raci_ref": "raci-procurement-ai-v1.0-public-draft",
  "accountable_party": "procurement-department-manager",
  "a2a_interaction_id": null,
  "retention_policy": "retain_7_years",
  "integrity_control": "append_only_log_with_hash_chain"
}
```

## 4. JSON Schema候補

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "AI Agent Audit Log Event v1.0 Public Draft",
  "type": "object",
  "required": [
    "audit_log_id",
    "event_timestamp",
    "event_type",
    "business_process_id",
    "referenced_standard_version",
    "agent_id",
    "agent_owner_id",
    "acting_on_behalf_of",
    "authority_scope",
    "prohibited_actions",
    "input_refs",
    "decision_summary",
    "output_refs",
    "rollback_policy",
    "risk_classification",
    "human_approval_status",
    "raci_ref",
    "accountable_party",
    "retention_policy"
  ],
  "properties": {
    "audit_log_id": { "type": "string" },
    "event_timestamp": { "type": "string", "format": "date-time" },
    "event_type": {
      "type": "string",
      "enum": ["read", "analyze", "suggest", "draft", "request_approval", "execute", "stop", "rollback", "exception"]
    },
    "business_process_id": { "type": "string" },
    "referenced_standard_version": { "type": "string" },
    "agent_id": { "type": "string" },
    "agent_owner_id": { "type": "string" },
    "acting_on_behalf_of": { "type": "string" },
    "authority_scope": {
      "type": "array",
      "items": {
        "type": "string",
        "enum": ["read", "analyze", "suggest", "draft", "request_approval", "execute_low_risk", "execute_with_approval", "prohibited"]
      }
    },
    "prohibited_actions": { "type": "array", "items": { "type": "string" } },
    "input_refs": { "type": "array", "items": { "type": "string" } },
    "context_refs": { "type": "array", "items": { "type": "string" } },
    "data_classification": { "type": "string" },
    "decision_summary": { "type": "string" },
    "output_refs": { "type": "array", "items": { "type": "string" } },
    "tool_calls": { "type": "array", "items": { "type": "object" } },
    "affected_records_ref": { "type": "array", "items": { "type": "string" } },
    "rollback_policy": { "type": "string" },
    "risk_classification": {
      "type": "string",
      "enum": ["low", "medium", "high", "highest", "prohibited"]
    },
    "human_approval_status": { "type": "string" },
    "approval_ref": { "type": ["string", "null"] },
    "sovereignty_gate_ref": { "type": ["string", "null"] },
    "raci_ref": { "type": "string" },
    "accountable_party": { "type": "string" },
    "a2a_interaction_id": { "type": ["string", "null"] },
    "retention_policy": { "type": "string" },
    "integrity_control": { "type": "string" }
  }
}
```

## 5. 実装時の最低ルール

- AIは監査ログの削除、改変、保管期間短縮を行えない
- ログは技術イベントだけでなく、委任元、権限、提案、承認、停止、RACIを含む
- 高リスク操作は承認ログと実行ログを接続する
- Human Sovereignty Gate対象は停止、凍結、再提案条件を記録する
- A2A連携は provider、consumer、usage_scope、liability_boundary、contract_ref を残す
- accountable_party にAIを入れない
