# Glossary

AI Agent Governance Commons v1.0 Public Draft で使う主要用語の定義をまとめる。

本用語集は法的定義ではない。RFP、設計書、監査ログ、RACI、Self-Assessment で解釈ブレを減らすための実務上の共通語彙である。

## 主要用語

| 用語 | 定義 | 注意点 |
| --- | --- | --- |
| AI Agent Governance Commons | AIエージェントを企業システム、SI、RFP、API、運用設計、監査設計に注入するための公共標準と実務テンプレート群 | 特定モデル、クラウド、ベンダー、OSSの仕様ではない |
| AIエージェント | 人間、部門、法人、業務プロセスの代理として、参照、分析、提案、下書き、承認依頼、低リスク実行補助などを行うAIシステム | 最終責任主体ではない |
| Minimum Viable Standard | AIエージェント導入時に最低限説明すべき10項目 | 安全認証や外部適合を意味しない |
| 最低説明項目 | RFP、設計書、監査ログ、RACI、Self-Assessment に転記すべき最小限の統治項目 | 説明できない場合、企業統制や監査に接続しにくい |
| Human-on-the-loop | AIの全処理を人間が逐一承認するのではなく、人間がリスクの高い判断、例外、不可逆操作、対外影響に集中する統治方式 | 全件承認ではない |
| Human Sovereignty Gate | 最高リスク操作や統治構造変更に対して、人間が最終的に停止、凍結、差し戻し、追加証跡要求を行える仕組み | AIが無効化できない停止権を含む |
| AI Agent RACI | AIエージェントが関与する業務の Responsible、Accountable、Consulted、Informed を分ける責任分界 | AIはAccountableにならない |
| Responsible | 実行、提案、処理、証跡提出などを担う主体 | AI、業務担当、SIer、AI提供者が入り得る |
| Accountable | 最終責任を負う主体 | 人間、業務部門、法人、委託先責任者などに置く |
| Consulted | 判断時に相談、参照される主体 | 監査、法務、専門家、専門AIなどが入り得る |
| Informed | 結果や判断を通知される主体 | 利用部門、監査、法務、顧客対応など |
| A2A責任分界 | AI同士、他部門AI、他社AI、外部AIサービス、委託先AIが連携する場合の利用範囲と責任境界 | 免責文ではなく、提供側と利用側の責任を分ける記録 |
| API Agent Context | AIがAPIを呼び出す際に、agent_id、acting_on_behalf_of、authority_scope、risk_classification などを付与する文脈情報 | 特定API仕様ではなく、説明可能性のための設計項目 |
| authority_scope | AIに許可される操作範囲 | read、analyze、suggest、draft、request_approval、execute_low_risk、execute_with_approval、prohibited など |
| prohibited_actions | AIが行ってはならない操作 | 本番DB直接更新、契約締結、送金、監査ログ改変、停止権無効化など |
| リスク分類 | AIの行為を低、中、高、最高、禁止行為に分ける分類 | 人間関与と監査ログ粒度を決める |
| 高リスク操作 | 金銭、契約、個人情報、対外影響、業務確定、不可逆操作に関わる操作 | 事前の人間承認を必須にする |
| 最高リスク操作 | 権限体系、監査ルール、停止権、ガバナンス構造の変更など | Human Sovereignty Gate の対象にする |
| 監査ログ | AIが誰の代理で、何を参照し、何を提案し、何を実行し、誰が承認または停止したかを復元する証跡 | AIの内部思考全文を保存するものではない |
| ロールバック | AIが関与した操作の取消、補正、復旧、通知、再処理 | 取消不能な操作は高リスクまたは最高リスクとして扱う |
| Self-Assessment | 企業または導入主体が、MVS v1.0 Public Draft の最低説明項目に回答できるかを自己点検すること | 安全保証、認証、準拠表示ではない |
| Evidence Package | RFP回答、設計書、監査ログ、RACI、Gate判断、A2A責任分界、Self-Assessmentの証跡参照を束ねる索引 | 安全認証ではなく、証跡の所在、状態、不足、レビュー責任を示す |
| Commons Change Control | Commons の標準項目の追加、改訂、廃止、状態変更を管理するための標準 | Commons 自体の統治を説明するために必要 |
| proposed | 標準候補として提案された状態 | 実務採用前の議論対象 |
| draft | 文書化され、レビュー中の状態 | まだ推奨状態ではない |
| recommended | v1.0 Public Draft内で推奨される状態 | 認証、適合、法的準拠を意味しない |
| deprecated | 非推奨化された状態 | 既存案件への移行期限や例外は別途管理する |

## 禁止または避ける表現

v1.0 Public Draft では、検証主体、基準、異議申し立て、監査手順が定義されるまで、以下の表現を避ける。

- Commons認証済み
- Commons適合
- Commons準拠により安全
- AIエージェント安全確認済み
- 外部監査済み

代わりに、以下のように表現する。

- MVS v1.0 Public Draft の最低説明項目について回答済み
- 参照したCommons標準版を明示済み
- 自己点検結果と証跡文書を提出可能

## 用語運用の原則

- AIは最終責任主体ではない
- 人間または法人のAccountableを必ず定義する
- 権限と禁止操作を同時に定義する
- 監査ログは技術ログだけでなく業務責任の証跡として扱う
- Evidence Package は証跡の束であり、安全保証や適合表示ではない
- Human Sovereignty Gate は全件承認ではなく最高リスク領域の停止権として扱う
- Self-Assessment を安全ラベルとして使わない
