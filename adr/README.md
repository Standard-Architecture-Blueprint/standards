# Design Guidelines

## 📌 概要
本ディレクトリは、特定のプログラミング言語や技術スタックに依存しない、システム全体の「設計原則」および「共通仕様」を定義する。

## 🎯 目的
1. **一貫性の確保**: 複数のリポジトリにまたがる開発において、設計思想の乖離を防ぐ。
2. **品質の標準化**: 業界標準（Best Practices）を明文化し、レビューコストを削減する。
3. **疎結合の維持**: 階層間の境界を定義し、変更に強いアーキテクチャを維持する。

## 🏛️ 主要ドキュメント
実装者は、開発着手前に以下のガイドラインを確認すること。

- **[Architecture Layers](./architecture-layers.md)**
  - SoE/SoR/Platform/SoI の役割分担と依存方向の定義。
- **[API Design Guidelines](./api-design-guidelines.md)**
  - RESTful API の命名規則、共通レスポンス、エラー構造の定義。
- **[Data Modeling Standards](./data-modeling-standards.md)**
  - DB命名規則、共通カラム、正規化指針、ER図の記述ルール。
- **[Integration Patterns](./integration-patterns.md)**
  - システム間連携（同期/非同期）、メッセージング、例外伝播のパターン。
- **[Security Design](./security-design.md)**
  - 認証・認可のシーケンス、暗号化基準、バリデーション方針。

## ⚖️ 運用ルール
- **設計変更の反映**: ADR で採択された新たな方針は、速やかに本ディレクトリの関連ドキュメントへ反映し、常に「現在の正解」に更新すること。
- **概念の優先**: 実装（Code）が本ガイドラインと矛盾する場合、原則として本ガイドラインを優先、またはガイドラインの修正を検討すること。

---
© 2026 Standard Architecture Blueprint.
