# MediaDo.go #1
- [MediaDo.go #1](https://mediado-go.connpass.com/event/140848/)
## レガシーシステムのサブシステムとしてGoを導入する - Clean Architectureの採用
- 方針
    - 改修
    - 新規
    - 漸進的に開発
- 作戦
    - ハードルを下げる
    - スケールを続けられる仕組み
- 手法
    - Go
    - マイクロサービス
- モノレポ
    - 1つのリポジトリで複数のモジュール（サービス・パッケージ）を管理
    - CI の設定必要
### GopherCon
- 初心者でも十分楽しめる
- MediaDo では社員負担ゼロで参加可能
### Reaserch
- クリーンアーキテクチャ
- マイクロサービス

## 駆け出しgopherがはじめてのバッチ設計で学んだこと
- AWS Batch
    - リソースの割り当てを管理
- AWS Step Functions
    - JSON 形式で作成
    - ワークフロー図 でバッチを管理（結果によって処理を場合分け）
    - ステップが遷移した回数に対する課金
### Go で詰まったこと
- `.env` をバイナリにできない
    - AWS コンソールで設定
    - `.env` 含めて zip ファイルを作成
    - アセットツール（statik、packr）を使用
### Research
- AWS Batch
- AWS Step Functions
- aws lambda


## パイプラインパターンでGoのバッチ処理をうまく並列化する
- コルーチンのリーク
    - 非メインのコルーチンが終了せず残り続ける
    - gc で回収されない
### バッチ処理の機会
- バッチ処理でユーザデータの不整合を解消
- ユーザからの個人情報の削除要請
- カラム追加時に既存レコードのデータ埋め
### 課題
- 処理量が多いので並行処理が複雑
- 可読性悪くてレビューがつらい
- ゴルーチン、チャネルがちゃんと使えているか不安

### Reference
- [Go Concurrency Patterns: Pipelines and cancellation](https://blog.golang.org/pipelines)
- [バッチ処理をパイプラインパターンで上手くやる](https://speakerdeck.com/yusukemisa/batutichu-li-wopaipurainpatandeshang-shou-kuyaru)
### Research
- パイプライン
- ファンイン

## テストを書こう
- コードの質を担保する方法
    - 静的解析, テスト, QA, 監視
    - 後ろに行く程つらくなる
- tenntenn はテストを別パッケージに書く
    - そのパッケージを使う側の気持ちで書ける
    - 使いづらいパッケージなのかどうか分かれば設計を見直せる
- テーブル駆動テスト
    - テストロジックとデータが分離することでコードが見やすくなる
### テスティングフレームワークを使わない理由
- Go の testing パッケージが多く使用される
    - あまりテストフレームワークを使わない
- テストは Go で書く
    - テストのための新しいミニ言語を作らない
### Reference
- [テストを書こう](https://docs.google.com/presentation/d/1aUMcNW7CMfXstDtKPQbMyfBz0sldp4yPbXvrJScYKvk/edit)
### Research
- サブテスト
- テーブル駆動テスト
