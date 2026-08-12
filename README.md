# imzipdoc

intra-mart **IM-LogicDesigner** のエクスポートZIP形式を解析してまとめた非公式ドキュメント集です。

IM-LogicDesignerは、GUIでロジックフローを組み立てる画面からデータをエクスポートすると、内部構造がほぼ非公開のZIPファイルとして出力されます。このリポジトリは、そのZIPの中身（JSON/XML構造）を実データから解析し、Bootstrap 5製の閲覧用HTMLドキュメントとしてまとめたものです。

## 公開ページ

[index.html](index.html) を起点に、対象ZIP形式ごとに4つのドキュメントへ分岐します。

| ドキュメント | 対象ファイル | 内容 |
| --- | --- | --- |
| [logicdesigner-zip-spec-flow.html](logicdesigner-zip-spec-flow.html)（フロー定義編） | `flow_definition.json` | ロジックフロー本体のZIP仕様。ZIP構造、フロー定義オブジェクト、`flowElements`、マッピング定義、デザイナ表示情報（`additional.ui`）、標準フロー要素早見表、新規ZIP生成手順 |
| [logicdesigner-zip-spec-userdef.html](logicdesigner-zip-spec-userdef.html)（ユーザ定義編） | `user_definition.json` | テナントに共有登録するユーザ定義タスクのZIP仕様。`definitionType`（sql・javascript・rest等）ごとの内部構造、新規ユーザ定義ZIP生成手順 |
| [logicdesigner-zip-spec-route.html](logicdesigner-zip-spec-route.html)（ルーティング定義編） | `flow_route.json` | フローをREST APIとして公開するルーティング設定のZIP仕様。認証方式、セキュアトークン、レスポンス種別など |
| [logicdesigner-zip-spec-related.html](logicdesigner-zip-spec-related.html)（関連機能編） | IM-Copilot / IM-JobScheduler | `assistant_definition.json`によるアシスタント登録、IM-JobScheduler連携によるスケジュール実行トリガ。IM-Copilot関連の標準フロー要素（`im_chat`等）はフロー定義編に記載 |

いずれもBootstrap 5（CDN読み込み）で作られた静的HTMLで、ビルド不要でブラウザから直接開けます。

## ドキュメントの性質

各ドキュメントは実際のZIPを解析した結果に基づいており、未確認・未検証の事項はその旨を明記しています。特定のサンプルのみに依存した記述は避け、一般化した仕様として記載する方針です（詳細は [AGENTS.md](AGENTS.md) の更新ルールを参照）。

製品バージョンやエクスポート対象によって項目の有無・挙動が異なる場合があるため、実運用にあたっては利用中のintra-mart環境で個別に確認してください。
