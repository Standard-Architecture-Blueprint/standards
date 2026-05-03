# Architecture Decision Records (ADR)

## 📌 概要
本ディレクトリは、プロジェクトにおける重要な技術的選定および設計判断の履歴を管理する。

## 🎯 目的
- **背景の保存**: 決定に至った技術的・ビジネス的背景を永続化する。
- **トレードオフの可視化**: 採用した案だけでなく、却下した案（Alternatives）とその理由を記録する。
- **継続的評価**: 過去の決定を、現在の技術状況に照らして再評価可能にする。

## 📋 ADR一覧 (Index)

| ID | Title | Status | Date |
|:---:|:---|:---:|:---:|
| 0000 | [ADRプロセスの定義](./0000-adr-process.md) | Accepted | 2026-05-03 |
| 0001 | [4階層アーキテクチャの採用](./0001-architecture-style.md) | Accepted | 2026-05-03 |
| 0002 | [バックエンド技術スタックの選定](./0002-select-backend-technology-stack.md) | Accepted | 2026-05-03 |
| 0003 | [フロントエンド技術スタックの選定](./0003-select-frontend-technology-stack.md) | Accepted | 2026-05-03 |
| 0004 | [データ永続化戦略](./0004-data-persistence-strategy.md) | Accepted | 2026-05-03 |
| 0005 | [認証・認可スキームの策定](./0005-authentication-and-authorization-scheme.md) | Accepted | 2026-05-03 |
| 0006 | [コンテナ・オーケストレーション戦略](./0006-container-orchestration-strategy.md) | Accepted | 2026-05-03 |

## 🛠 運用フロー
1. `../templates/adr-template.md` をコピー。
2. `NNNN-title-in-kebab-case.md` の形式で命名。
3. Status を `Proposed` で PR 作成。
4. 承認後、Status を `Accepted` に変更してマージ。

---
© 2026 Standard Architecture Blueprint.
