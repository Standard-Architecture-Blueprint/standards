# Design Guidelines (システム設計指針)

## 📌 概要
本ディレクトリは、システム全体で一貫性を保つための「基本設計の共通ルール」を定義する。ADRで決定されたアーキテクチャ方針を具体化し、特定のリポジトリや言語に閉じない汎用的な設計規律を記述する。

## 🎯 目的
1. **設計の標準化**: 複数のリポジトリ群において、どこに何を書くべきかの迷いを排除する。
2. **インターフェースの整合**: SoE（フロント）と SoR（バック）間の「対話の作法」を統一する。
3. **品質の均質化**: 開発者のスキルに依存せず、エンタープライズ級の堅牢性を確保する。

## 🏛️ 主要ガイドライン一覧

| ファイル名 | 定義内容の要約 | 関連する知識体系 |
|:---|:---|:---|
| [architecture-layers.md](./architecture-layers.md) | 4階層（SoE/SoR/Platform/SoI）の責務と依存関係の定義 | クリーンアーキテクチャ, DDD |
| [api-design-guidelines.md](./api-design-guidelines.md) | RESTful API のエンドポイント、メソッド、共通レスポンス形式 | Web API デザイン |
| [data-modeling-standards.md](./data-modeling-standards.md) | DB命名規則、共通カラム（監査用）、インデックス設計指針 | リレーショナルモデル, 正規化 |
| [integration-patterns.md](./integration-patterns.md) | 同期・非同期連携、メッセージング、エラー伝播のパターン | エンタープライズ統合パターン |
| [security-design.md](./security-design.md) | 共通バリデーション方針、認証トークン伝播、認可モデル | OWASP, ゼロトラスト |

## ⚖️ 運用指針
- **原則の継承**: すべての設計は `adr/` で決定された意思決定を上位概念として継承すること。
- **実装への架け橋**: 本ディレクトリで定義された「ルール」は、`engineering/` において具体的なコード（Java/TypeScript等）として実装される。
- **更新のトリガー**: 新しい設計パターンを導入する場合は、まず ADR で議論し、承認後に本ディレクトリを更新すること。

---
© 2026 Standard Architecture Blueprint.
