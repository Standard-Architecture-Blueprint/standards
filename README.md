# Architecture Standards & Guidelines (ASG)

> **"Standardization of architectural decisions and engineering principles."**  
> 本リポジトリは、プロジェクト全体のアーキテクチャ一貫性を保持するための、技術標準、意思決定記録（ADR）、および再利用可能なプロジェクトテンプレートの中央管理場所である。

---

## 📌 目的
本リポジトリは、ISO/IEC 42010 に準拠したアーキテクチャ記述の標準化、およびプロジェクトにおける技術的ガバナンスの確立を目的とする。すべての実装リポジトリ（計13リポジトリ）は、本ガイドラインを参照し、定義された制約事項を遵守しなければならない。

## 🏛️ ディレクトリ構成

### 1. [ADR (Architecture Decision Records)](./adr/)
技術選定および設計判断の履歴を管理する。
- 業界標準の [MADR](https://github.com/adr/madr) 形式を採用。
- 決定に至る背景、代替案との比較、およびその結果生じる制約を記録する。

### 2. [Design Guidelines](./design/)
- **Domain Modeling**: エンティティ定義、境界付けられたコンテキスト、データ整合性方針。
- **Interface Design**: RESTful API 規約、共通レスポンス、エラーコード仕様。
- **Layered Architecture**: SoE/SoR 分離、依存関係の方向、インターフェース分離。

### 3. [Engineering Standards](./engineering/)
- **Backend Standard**: Java/Spring Boot におけるデザインパターン、例外ハンドリング規約。
- **Frontend Standard**: コンポーネント設計、状態管理（RxJS）、デザインシステム（Tailwind）。
- **Security Standard**: OAuth 2.0 / JWT 準拠の実装フロー、機密情報管理。

### 4. [Operations & Infrastructure](./ops/)
- **Containerization**: Dockerfile マルチステージビルド基準、共通ベースイメージ。
- **Observability**: 構造化ログフォーマット、メトリクス収集、分散トレーシング規約。

### 5. [Templates](./templates/)
新規リポジトリ作成時に使用する、応用情報技術者試験（AP）の知識体系に基づいた標準雛形。
- **[backend-spring-boot](./templates/backend-spring-boot/)**: Layered Architectureを採用したJava基盤。
- **[frontend-angular](./templates/frontend-angular/)**: モジュール独立性を高めたSPA基盤。
- **[common-library](./templates/common-library/)**: 全サービスで共有する基盤ロジック（例外、ログ、共通モデル）。
- **[github-actions](./templates/github-actions/)**: CI/CDパイプライン（Build/Test/Deploy）の自動化定義。

## 📝 開発プロセス
1. **設計判断**: 重要な変更は `adr/` にて提案・承認を受ける。
2. **プロジェクト開始**: `templates/` をベースに新規リポジトリを生成する。
3. **共通化**: 業務を跨ぐ共通機能は `common-library` へ集約し、重複開発を排除する。

## ⚖️ 準拠性 (Compliance)
- **Traceability**: すべての実装は、本リポジトリの ADR および各 Template の規約に紐付いていなければならない。
- **Evolutionary Architecture**: 技術トレンドの変化に応じ、テンプレートおよび決定事項は `Superseded`（代替済み）として適切に更新管理される。

---
© 2026 Standard Architecture Blueprint. Managed by System Architect.
