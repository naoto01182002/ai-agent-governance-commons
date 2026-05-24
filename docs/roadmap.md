# Roadmap

AI Agent Governance Commons は、思想を完全に完成させてから公開するのではなく、実務で使える標準パッケージを段階的に育てる。

## バージョン方針

| 段階 | ゴール | 終了条件 |
| --- | --- | --- |
| v1.0 Public Draft | Initial Public Release | 最低限の標準項目と実務テンプレートが一通り揃い、外部の人が読んで使える |
| v1.1 | 実務適用版 | RFP、設計書、監査、RACIに実際に貼った結果を受けて粒度を磨く |
| v2.0 | 公開標準候補版 | 外部レビュー、利用例、変更管理を受けて、より安定した参照標準にする |

## v1.0 Public Draft 完成判定

v1.0 Public Draft は、以下が揃った時点で一区切りとする。

| 成果物 | 完成条件 | 現在の文書 |
| --- | --- | --- |
| 方針書 | 構想の目的、対象、非対象が説明されている | `docs/policy/ai-agent-governance-commons-policy.md` |
| Minimum Viable Standard | 最低説明10項目が確定している | `docs/standards/minimum-viable-standard-v1.0.md` |
| 標準化方針 | 権限、リスク、監査、RACI、A2Aが横断整理されている | `docs/standards/standardization-principles.md` |
| 用語集 | 主要概念の定義が揃っている | `docs/glossary.md` |
| RFP追補 | ベンダーに回答させる質問、証跡、最低失格条件がある | `docs/templates/rfp-governance-addendum.md` |
| RFP追補別紙 | RFPにそのまま貼れる短縮版がある | `docs/templates/rfp-addendum-template.md` |
| 設計書テンプレート | 要件定義、API、運用設計に転記できる | `docs/templates/ai-agent-governance-design-template.md` |
| 監査ログ項目表 | 必須ログ項目が表で定義されている | `docs/templates/ai-agent-audit-log-template.md` |
| 監査ログ標準 | JSON例とJSON Schema候補がある | `docs/templates/audit-log-standard.md` |
| RACIテンプレート | AIがAccountableにならない構造が示されている | `docs/templates/ai-agent-raci-template.md` |
| A2A責任分界 | AI間、企業間連携の責任境界が書ける | `docs/templates/ai-agent-a2a-responsibility-boundary-template.md` |
| A2A責任境界別紙 | 構造化メッセージと契約別紙への転記例がある | `docs/templates/a2a-liability-boundary-template.md` |
| Self-Assessment | 導入前に自己診断できる | `docs/templates/self-assessment-checklist.md` |
| Human Sovereignty Gate | 停止権、凍結、再提案、例外不可条件が運用できる | `docs/templates/human-sovereignty-gate-operating-template.md` |
| Evidence Package | RFP、設計書、監査ログ、RACI、Self-Assessmentの証跡対応を束ねられる | `docs/templates/ai-agent-evidence-package-template.md` |
| Release Readiness | v1.0 Public Draft対象文書と公開前チェックを確認できる | `docs/release-readiness-v1.0.md` |
| サンプル案件 | テンプレートの使い方を具体例で確認できる | `docs/examples/procurement-ai-agent-example.md` |
| 利用条件 | 公開標準としての利用条件と非認証表示を確認できる | `LICENSE.md` |
| 公開README | 初見の人が使い方を理解できる | `README.md` |
| 公開用manifest | docs-only公開repoに含める対象が分かる | `docs/publication/public-repository-manifest.md` |
| 公開計画 | GitHub、note、X、LinkedIn、後続媒体の役割が分かる | `docs/publication/public-launch-plan-v1.0.md` |
| Decision Log | 重要判断への公開入口がある | `docs/decision-log.md` |

## v1.0 Public Draft で目指すこと

- RFP追補テンプレートとして使われる
- SIerの提案、設計標準に組み込める
- 企業の社内標準、チェックリストに入れられる
- 内部監査、法務、情シスが参照できる
- 監査法人、保険会社、業界団体へ議論材料として渡せる

## v1.0 Public Draft で目指さないこと

- 認証ビジネス
- OSS実装
- AIエージェント基盤そのもの
- 全業界対応の完全標準
- 法的に厳密な規格
- 特定モデル、特定クラウド、特定ベンダーの仕様化

## v1.1 候補

v1.1 では、v1.0 Public Draft を実務で貼れる粒度へ磨く。

- 業界別または案件規模別のRFP配点例
- Evidence Package の証跡粒度を、業界別または案件規模別の提出範囲へ具体化する
- 契約別紙、委託先管理台帳、監査調書への接続文言
- Human Sovereignty Gate の停止理由コード、例外理由コードの整理
- 承認疲労指標とレビュー頻度の実務例
- A2A責任分界の複数段連携例
- 監査ログ保存期間と改ざん防止の考え方
- 外部専門家、監査法人、保険会社が関与する場合の責任範囲
- 初回公開後の反応を踏まえたZenn、Qiita、GitHub Pages展開

## v2.0 候補

v2.0 では、v1.0 Public Draft と v1.1 で得た外部フィードバックを踏まえ、より安定した公開標準候補として整える。

- v1.0 Public Draft、v1.1利用者からのフィードバック反映
- 文書間の用語、ID、参照関係の安定化
- change control の運用手順明確化
- 公開レビュー手順と反対意見の記録方式
- 外部表示ルールの明確化
- 参照実装ではなく、参照テンプレートとしての配布形式整備

## 継続判断

v1.0 Public Draft が揃った後は、考えるフェーズを延長し続けない。

次の作業は、完全性の追求ではなく、RFP、設計書、監査、RACIへ実際に貼ったときの不足を受けて改善する段階とする。
