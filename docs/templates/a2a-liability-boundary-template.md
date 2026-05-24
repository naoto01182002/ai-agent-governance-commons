# A2A Liability Boundary Template v1.0 Public Draft

この文書は、AIエージェント同士、他部門AI、他社AI、外部AIサービス、委託先AIが連携する場合の責任境界を、設計書、契約別紙、委託先管理台帳、監査ログへ転記するための配布用テンプレートである。

詳細版は `docs/templates/ai-agent-a2a-responsibility-boundary-template.md` を参照する。

## 1. 基本原則

A2A連携では、提供側AIの出力を、利用側がそのまま業務確定に使わない。

提供側は、出所、鮮度、利用範囲、禁止用途、責任境界、障害時連絡先を示す。

利用側は、自社の業務文脈、権限、契約、監査ログ、RACIに基づき、再判断責任を負う。

AIは提供側でも利用側でもAccountableにはならない。最終責任は人間、法人、業務オーナー、委託先責任者、契約上の責任主体に置く。

## 2. A2A責任境界表

| 項目 | 記入内容 |
| --- | --- |
| a2a_boundary_id |  |
| provider_agent_id |  |
| provider_owner |  |
| consumer_agent_id |  |
| consumer_owner |  |
| response_type | 情報提供、分析、提案、下書き、分類、実行要求など |
| data_source |  |
| data_timestamp |  |
| valid_until |  |
| usage_scope |  |
| not_authorized_for |  |
| liability_boundary |  |
| consumer_responsibility |  |
| contract_ref |  |
| incident_contact |  |
| audit_log_id |  |
| human_approval_required | Yes / No |
| sovereignty_gate_required | Yes / No |
| raci_ref |  |

## 3. 構造化メッセージ例

```yaml
a2a_boundary_id: a2a-20260523-001
provider_agent_id: supplier-risk-agent
provider_owner: vendor-risk-service-provider
consumer_agent_id: procurement-agent
consumer_owner: procurement-department
response_type: supplier_risk_summary
data_source:
  - supplier-risk-database
  - sanctions-screening-feed
data_timestamp: 2026-05-23T08:00:00+09:00
valid_until: 2026-06-22T23:59:59+09:00
usage_scope:
  - internal_supplier_review
  - purchase_request_draft
not_authorized_for:
  - contract_execution
  - payment_execution
  - public_disclosure
  - automated_supplier_blacklisting
liability_boundary: >
  Provider is responsible for the stated data source, timestamp, and service availability
  within the referenced contract. Consumer is responsible for business use, approval,
  final supplier decision, external communication, and rollback.
consumer_responsibility:
  - verify_supplier_context
  - apply_internal_procurement_policy
  - obtain_human_approval_for_high_risk_decisions
contract_ref: contract-vendor-risk-2026
incident_contact: vendor-risk-incident@example.com
audit_log_id: audit-20260523-a2a-001
human_approval_required: true
sovereignty_gate_required: false
raci_ref: raci-procurement-ai-v1.0-public-draft
```

## 4. 契約別紙への転記例

以下は契約条項そのものではなく、契約別紙や委託先管理台帳へ転記するための実務文である。法的効力を持たせる場合は各社法務で確認する。

```text
AIエージェント間連携において、提供側は、提供する出力の出所、データ時点、利用可能範囲、利用禁止用途、障害時連絡先、提供ログ参照を示す。

利用側は、提供側AIの出力を自社業務に利用する前に、利用範囲、禁止用途、データ鮮度、権限、リスク分類、人間承認要否を確認する。

提供側AIの出力は、利用側の契約締結、送金、与信確定、価格確定、対外通知、業務確定を自動的に正当化しない。

利用側は、自社業務への利用判断、承認、対外説明、取消または復旧について、利用側のRACIと監査ログに基づき説明責任を負う。
```

## 5. 利用禁止用途の例

| 禁止用途 | 理由 |
| --- | --- |
| 契約締結の自動確定 | 法的・金銭的影響が大きい |
| 送金、支払、返金の自動実行 | 取消困難な金銭影響がある |
| 与信、採用、処分の自動確定 | 人権、法務、説明責任に関わる |
| 個人情報または機密情報の外部送信 | データ保護と委託先管理に関わる |
| 監査ログ削除、改変、保管期間短縮 | 監査可能性を破壊する |
| Human Sovereignty Gateの無効化 | 人間停止権を破壊する |

## 6. 利用側レビュー

| 確認項目 | Yes/No | 証跡 |
| --- | --- | --- |
| provider_agent_id と provider_owner が明示されている |  |  |
| usage_scope と not_authorized_for が明示されている |  |  |
| valid_until または再確認条件がある |  |  |
| consumer_responsibility が定義されている |  |  |
| contract_ref または委託先管理参照がある |  |  |
| incident_contact がある |  |  |
| 利用側の再判断ログを残す |  |  |
| 高リスク利用時に人間承認がある |  |  |
| AIをAccountableにしていない |  |  |

## 7. 最低重大未解消条件

以下に該当するA2A連携は、重大未解消条件として扱う。

- provider と consumer の責任主体が不明である
- usage_scope と not_authorized_for が定義されていない
- 利用側の再判断責任がない
- contract_ref、委託先管理参照、incident_contact がない
- A2A監査ログがなく、提供、利用、再判断、承認を復元できない
- AIを提供側または利用側のAccountableに置いている
- 高リスク操作にA2A出力を使うが、人間承認またはHuman Sovereignty Gateがない
