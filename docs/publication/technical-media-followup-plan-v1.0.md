# Technical Media Follow-up Plan v1.0 Public Draft

## 1. 位置づけ

Zenn、Qiita、GitHub Pagesは、v1.0 Public Draft の初回公開後に追加する後続導線として扱う。

初回公開ではGitHub、GitHub Release、note、X、LinkedInを優先する。技術媒体は、標準本文を公開した後、読者の関心が見えた論点から順に書く。

## 2. Zenn記事案

Zennは、技術者、SIer、アーキテクト向けに、標準をどう実務文書へ落とすかを扱う。

| 優先 | 記事テーマ | 狙い |
| --- | --- | --- |
| 1 | AIエージェント時代のRFPに何を書くべきか | 調達、提案、要件定義への入口 |
| 2 | AIエージェントの監査ログに残すべき項目 | 実装者、アーキテクト向け |
| 3 | AIをAccountableにしないRACI設計 | 責任分界を設計へ落とす |
| 4 | Human-in-the-loopでは足りない。Human-on-the-loopで設計する | 承認疲れとリスクベース統制 |
| 5 | A2A連携で責任境界を消さないための設計 | 外部AI、委託先AI、他社AI連携 |

## 3. Qiita記事案

Qiitaは、業務システム実装に近い話題へ寄せる。

| 優先 | 記事テーマ | 狙い |
| --- | --- | --- |
| 1 | AIエージェント監査ログのJSON項目例 | 実装者が使いやすい入口 |
| 2 | AIに本番DBを直接更新させない設計パターン | 業務API、承認、取消の整理 |
| 3 | AI Agent ContextをAPI設計へ入れる | API設計、認可、ログへの接続 |
| 4 | Self-Assessmentを運用開始判定に使う | 情シス、監査向け |

## 4. GitHub Pages案

GitHub Pagesは、初回公開後にREADMEだけでは読みにくい場合に追加する。

| ページ | 内容 |
| --- | --- |
| Home | 何の標準か、何ではないか |
| Start Here | 読者別の使い方 |
| Minimum Viable Standard | 必須10項目 |
| Templates | RFP、設計書、監査ログ、RACI、A2A、Self-Assessment |
| Example | 調達AIエージェント例 |
| Release Readiness | 公開版の対象と対象外 |
| License | 利用条件と非認証表示 |

## 5. 後続展開の判断基準

| 判断軸 | GitHub Pages化する条件 |
| --- | --- |
| READMEが長くなりすぎる | 読者別導線がREADMEだけでは追いにくい |
| 経営層、法務、監査へ見せたい | GitHub UIよりWebドキュメントが向く |
| 外部リンクされ始める | 安定した読み物URLが必要 |
| テンプレートが増える | ナビゲーションが必要 |

## 6. 注意点

- GitHub Pagesは正本ではなく読み物版とする
- 正本はGitHub repoとReleaseに置く
- Pagesには認証、準拠、安全保証ではない旨を各入口に置く
- PagesとGitHub Releaseの版ずれを避ける
