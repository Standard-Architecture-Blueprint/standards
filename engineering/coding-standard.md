# コーディング規約 (Coding Standard)

## 📌 概要
本ドキュメントは、Standard Architecture Blueprint (SAB) におけるソースコードの実装基準を定める。AP試験の「ソフトウェア保守」の指標に基づき、誰が読んでも理解可能で、変更による影響範囲が特定しやすい「クリーンなコード」の生成を目的とする。

## 1. 命名規則 (Naming Convention)
AP試験の「保守性」を高めるための最重要項目として、以下の標準を採用する。

- **基本原則**: 略語を避け、目的が明確な単語を選択する（例: `ret` ではなく `result`, `d` ではなく `daysPassed`）。
- **クラス / インターフェース**: PascalCase (例: `OrderService`, `IUserRepository`)。
- **メソッド / 関数**: camelCase (例: `calculateTax`, `isValidUser`)。
- **変数**: camelCase (例: `totalAmount`)。
- **定数**: UPPER_SNAKE_CASE (例: `MAX_CONNECTION_POOL`)。
- **Booleans**: `is`, `has`, `can` 等の助動詞を接頭辞とし、真偽値であることが一目でわかるようにする。

## 2. 例外処理 (Exception Handling)
AP試験の「堅牢性」および「信頼性」の概念に基づき、エラー発生時の挙動を予測可能にする。

- **BaseException の継承**: プロジェクト共通の `BaseException` を定義し、ドメイン固有のエラー（`UserNotFoundException` 等）はこれを継承する。
- **エラー情報の付与**: すべての例外には「エラーコード」と「原因（Cause）」を内包させ、デバッグ効率を最大化する。
- **投げっぱなしの禁止**: catch ブロックで例外を握り潰す（ログも出さずに無視する）ことを厳禁とする。
- **不変条件のチェック**: 関数の入り口で引数の妥当性を検証し（Guard Clause）、異常な状態での実行を即座に中断させる。

## 3. ログ出力標準 (Logging Standard)
AP試験の「システム監査」および「運用管理」における証跡（エビデンス）管理を目的とする。

- **ログレベルの使い分け**:
  - `ERROR`: 継続不能な異常。即時通知対象。
  - `WARN`: 業務上の例外や、リトライ可能な一時的エラー。
  - `INFO`: システムの正常な状態遷移（リクエストの受理、処理の完了）。
  - `DEBUG`: 開発・トラブルシューティング用の詳細情報。
- **構造化ログ**: JSON形式で出力し、全ログに `trace_id` を付与することで、13のリポジトリを跨ぐリクエストの追跡を可能にする。
- **機密情報の除外**: 個人情報（PII）やパスワード、トークンなどはマスク処理を施し、ログに記録しない。

## 4. プログラム構造の原則
AP試験の「モジュール設計」における評価指標（結合度・強度）を最適化する。

- **単一責任原則 (SRP)**: 1つのクラス、1つの関数は、1つのことだけを行う。
- **関数の長さ**: 1つの関数は原則として30行以内、インデントの深さは2階層までを目安とし、読みやすさを維持する。
- **定数値の定数化**: マジックナンバー（意味不明な数値）を直接記述せず、必ず名前付き定数として定義する。

---
"Readability is the primary goal. Performance is the byproduct of Clean Code."
© 2026 Standard Architecture Blueprint. Managed by System Architect.
