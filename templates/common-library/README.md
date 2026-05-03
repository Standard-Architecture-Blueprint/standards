# Common Library (共通基盤ライブラリ)

## 📌 概要
本プロジェクトは、13のマイクロサービス群すべてで共有される基盤ロジックを管理するライブラリである。応用情報技術者試験（AP）における「モジュールの再利用」と「インターフェースの標準化」の原則に基づき、システム全体の品質を均一化する。

## 📂 ディレクトリ構造と役割
各モジュールは、特定の業務ロジック（ドメイン知識）を持たず、純粋な「基盤機能」に徹すること。
```text
src/main/java/com/example/common/
├── api/              # 【Interface Standardization】
│   │                 # 全サービス共通の通信プロトコルを定義。
│   ├── response/     # ApiResponse<T>、PagedResponse等の共通フォーマット。
│   └── constants/    # エラーコード、HTTPステータスコードの共通定数。
│
├── auth/             # 【Security & Identity】
│   │                 # 認証・認可に関する横断的ロジック。
│   ├── model/        # サービス間を伝搬するAuthenticatedUserなどの共通モデル。
│   └── context/      # SecurityContextからユーザー情報を抽出する共通ユーティリティ。
│
├── exception/        # 【Error Handling】
│   │                 # システム全体で統一すべき例外クラスの定義。
│   ├── base/         # 全例外の基底となるBaseException。
│   └── types/        # NotFound, Validation, Unauthorized等の具体的例外。
│
├── logging/          # 【Cross-Cutting Concerns】
│   │                 # 分散トレーシングとログの標準化。
│   ├── aspect/       # メソッド実行時間や入出力を自動記録するAOP。
│   └── filter/       # リクエスト毎にTrace-IDを採番するサーブレットフィルタ。
│
└── util/             # 【General Utilities】
    │                 # 業務ロジックを含まない、純粋な汎用処理。
    ├── date/         # 日時計算、JST/UTC変換などの共通処理。
    └── json/         # Jacksonのカスタマイズ設定やシリアライズ補助。
```
## 🛠️ 技術スタック
- **Java 17 / Spring Boot 3.x Starter**: 基盤技術の統一。
- **Maven/Gradle**: 他のリポジトリから依存関係として参照される。
- **Lombok**: ボイラープレートコードの削減。

## 📐 実装・運用規約
AP試験の「構成管理」および「変更管理」に基づき、以下のルールを適用する。

1. **破壊的変更の禁止**: 
   - 共通ライブラリの変更は全リポジトリに影響するため、後方互換性を厳格に維持する。
2. **業務ロジックの混入禁止**: 
   - 特定のサービス（例：銀行振込、ユーザー登録）に依存するコードは書かない。
3. **バージョン管理の徹底**: 
   - Semantic Versioning (例: 1.2.3) を遵守し、マイナーアップデートのみを許容する。

## 🚀 利用方法
各プロジェクトの `pom.xml` または `build.gradle` にて、本ライブラリを依存関係に追加すること。
```xml
<dependency>
    <groupId>com.example</groupId>
    <artifactId>common-library</artifactId>
    <version>${common.version}</version>
</dependency>
```
## 🧪 品質管理
- 共通部品としての「信頼性」を担保するため、単体テストによる**命令網羅（C0）100%** を維持する。

---
© 2026 Standard Architecture Blueprint.
