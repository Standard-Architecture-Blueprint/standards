# Architecture Standards & Guidelines (ASG)

> **"Standardization of architectural decisions and engineering principles."**  
> 本リポジトリは、プロジェクト全体のアーキテクチャ一貫性を保持するための、技術標準および意思決定記録（ADR）の中央管理場所である。

---

## 📌 目的
本リポジトリは、ISO/IEC 42010 に準拠したアーキテクチャ記述の標準化、およびプロジェクトにおける技術的ガバナンスの確立を目的とする。すべての実装リポジトリは、本ガイドラインを参照し、定義された制約事項を遵守しなければならない。

## 🏛️ ディレクトリ構成

### 1. [ADR (Architecture Decision Records)](./adr/)
技術選定および設計判断の履歴を管理する。
- 業界標準の [MADR](https://github.com/adr/madr) 形式を採用。
- 決定に至る背景、代替案との比較、およびその結果生じる制約を記録する。

### 2. [Design Guidelines](./design/)
- **Domain Modeling**: エンティティ定義、境界付けられたコンテキスト、データ整合性方針。
- **Interface Design**: RESTful API 規約、ステータスコード定義、ヘッダー仕様。
- **Layered Architecture**: SoE/SoR 分離、依存関係の方向、インターフェース分離の原則。

### 3. [Engineering Standards](./engineering/)
- **Backend Standard**: Java/Spring Boot におけるデザインパターン、例外ハンドリング。
- **Frontend Standard**: コンポーネント設計、状態管理、レンダリング戦略。
- **Security Standard**: OAuth 2.0 / OIDC 準拠の実装フロー、機密情報管理。

### 4. [Operations & Infrastructure](./ops/)
- **Containerization**: Dockerfile マルチステージビルド、ベースイメージの選定基準。
- **Observability**: ログフォーマット、メトリクス収集、分散トレーシング。

## 📝 アーキテクチャ意思決定（ADR）のプロセス
重要な設計変更や技術選定を行う際は、以下のフローを遵守する。
1. **Proposed**: 提案。ADRドラフトを作成し、Pull Request を提出する。
2. **Review**: 妥当性、互換性、将来の保守性についてレビューを行う。
3. **Accepted**: 承認。マージ後、決定事項として全リポジトリに適用される。

## ⚖️ 準拠性 (Compliance)
- **Traceability**: すべての実装は、本リポジトリの ADR と紐付いていなければならない。
- **Evolutionary Architecture**: 技術トレンドや要件の変化に応じ、既存の決定事項は `Superseded`（代替済み）として適切に更新・管理される。

---
© 2026 Standard Architecture Blueprint. Managed by System Architect.
