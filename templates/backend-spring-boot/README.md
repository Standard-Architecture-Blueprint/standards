# Backend Spring Boot Project Template

## 📌 概要
本プロジェクトは、複数のマイクロサービス群におけるバックエンド開発の標準雛形である。応用情報技術者試験（AP）で定義される「ソフトウェア設計（内部設計）」の原則に基づき、保守性、拡張性、および再利用性を最大化した階層化アーキテクチャを採用している。

## 📂 ディレクトリ構造と役割
AP試験の「モジュール独立性（高凝集・低結合）」を実現するため、以下のパッケージ構成を厳守すること。
```text
src/main/java/com/example/template/
├── controller/       # 【Presentation Layer】
│   │                 # 外部IF(REST)の定義、リクエストバリデーション、
│   │                 # DTO(Data Transfer Object)とドメインモデルの変換。
│   └── dto/          # リクエスト/レスポンスのデータ構造定義。
│
├── service/          # 【Application Layer】
│   │                 # 業務ロジックの実行、トランザクション境界の管理。
│   │                 # 複数のドメインモデルを組み合わせたユースケースの実装。
│   └── exception/    # 業務例外（Business Exception）の定義。
│
├── domain/           # 【Domain Layer】
│   ├── model/        # エンティティ(Entity)、値オブジェクト(Value Object)。
│   └── repository/   # リポジトリインターフェース（実装はinfrastructure層）。
│
├── infrastructure/   # 【Infrastructure Layer】
│   ├── repository/   # DBアクセス(JPA/MyBatis)の具体的実装。
│   └── external/     # 外部APIクライアント、メッセージング通信の実装。
│
└── common/           # 【Cross-Cutting Concerns】
    ├── aspect/       # AOPによる共通ロギング、性能計測。
    ├── config/       # Bean定義、セキュリティ、CORS設定。
    └── handler/      # 全局的な例外ハンドリング(RestControllerAdvice)。
```
## 🛠️ 技術スタック（デファクトスタンダード）
応用情報技術者試験（AP）の「標準化」および「開発環境」の知識体系に基づき、業界標準のライブラリを選定。13リポジトリすべてでこのバージョンを統一（BOM管理）する。

| カテゴリ | 選定技術 | 理由・AP試験との関連 |
|:---|:---|:---|
| **Language** | Java 17 (LTS) | 封印クラス(Sealed Class)やRecord型による**保守性**の向上。 |
| **Framework** | Spring Boot 3.x | **依存性の注入 (DI)** によるコンポーネント間の低結合化を実現。 |
| **Security** | Spring Security | **認証・認可**の分離。JWTを用いたステートレスなセキュリティ。 |
| **Persistence** | Spring Data JPA | **ORM (Object-Relational Mapping)** によるデータアクセスの抽象化。 |
| **Validation** | Hibernate Validator | **入力バリデーション**の宣言的記述（Bean Validation）。 |
| **Documentation** | SpringDoc OpenAPI | **インターフェース設計書**の自動生成（Swagger UI）。 |
| **Utility** | Lombok / MapStruct | **ボイラープレートコード**を排除し、コードの可読性を向上。 |
| **Testing** | JUnit 5 / Mockito | **単体テスト**および**テストダブル**（モック）の標準。 |

## 📐 実装規約 (Implementation Rules)
AP試験の「ソフトウェア品質特性（機能適合性、保守性）」を確保するための5原則。

1. **ステートレス性の維持**: 
   - スケーラビリティ確保のため、`HttpSession` 等のサーバーサイドセッションは使用禁止。
2. **バリデーションの2層防御**: 
   - `Controller` 層で形式チェック（型・必須）、`Service` 層で論理チェック（整合性）を実施。
3. **例外処理の共通化**: 
   - `common/handler` にて例外を一括キャッチし、ログ出力とレスポンス変換を自動化する。
4. **DTO의徹底活用**: 
   - `Entity`（DB構造）を直接外部へ公開しない。必ず `DTO` へ変換してレスポンスする。
5. **トランザクション制御**: 
   - 業務のひとかたまり（原子性：ACID特性）を `Service` 層のメソッド単位で `@Transactional` 管理する。

## 🚀 セットアップ手順
1. **環境変数の設定**: 
   - `.env.example` をコピーして `.env` を作成。DB接続情報を記述する。
2. **ビルドと依存関係の解決**:
   ```bash
   ./mvnw clean install
3. **アプリケーションの起動**:
   ```bash
   ./mvnw spring-boot:run -Dspring-boot.run.profiles=local
4. **APIドキュメントの確認**:
   - 起動後、`http://localhost:8080/swagger-ui/index.html` にて定義を確認可能。

## 🧪 テスト実施指針
AP試験の「テスト手法」に基づき、品質を定量的に管理する。

- **単体テスト (Unit Test)**:
  - 対象: `Service` 層、`Domain` 層。
  - 網羅性: 判定条件網羅（C1）80% 以上を目標とする。
- **結合テスト (Integration Test)**:
  - 対象: `Controller` 層 ＋ `Database`。
  - 手法: `Testcontainers` を使用し、Docker上の本物のDBに対してSQLを発行する。

---
© 2026 Standard Architecture Blueprint.
