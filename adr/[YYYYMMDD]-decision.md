# YYYYMMDD-Service-Communication-Protocol

*   **Status**: Accepted
*   **Deciders**: System Architect
*   **Date**: 2026-05-04
*   **Related Requirements**: REQ-010 (マイクロサービス間の低遅延通信), REQ-015 (スキーマ定義の厳格化)

## 1. Context (背景と課題)
13のリポジトリ（マイクロサービス）間で発生する通信をどう定義するか。現状、開発効率を優先して REST が検討されているが、医療系ドメインへの将来的な展開を見据えると、データ整合性とパフォーマンスの両立が必須である。

## 2. Decision Driver (決定要因)
1. **型安全性**: 通信インターフェースの不一致によるランタイムエラーの防止（AP試験：信頼性）。
2. **パフォーマンス**: 大量データ送受信時の低遅延（AP試験：効率性）。
3. **エコシステム**: TypeScript(Frontend) と Java(Backend) での親和性。

## 3. Considered Options (検討した代替案)
- **Option A**: JSON over REST (Spring Web)
- **Option B**: gRPC (Protocol Buffers)
- **Option C**: GraphQL

## 4. Pros and Cons of the Options (各案のメリット・デメリット)

### Option A: JSON over REST
- **Pros (+)**: 開発者が慣れており、デバッグ（cURL/Postman）が極めて容易。
- **Cons (-)**: 型定義が緩く、クライアント/サーバー間のスキーマ齟齬が発生しやすい。JSONのパース負荷が高い。

### Option B: gRPC
- **Pros (+)**: Protocol Buffers による強力な型定義。HTTP/2 による高速なバイナリ通信。
- **Cons (-)**: ブラウザ直接通信にプロキシ(gRPC-Web)が必要。バイナリのため人間による目視デバッグが困難。

## 5. Decision Outcome (決定事項)
- **Chosen Option**: **Option B (gRPC)**
- **Rationale**: 13のリポジトリを統治する上で、通信エラーは最大の「不確実性」である。Protocol Buffers により「契約（Contract）」をコードレベルで強制することが、AP試験の「信頼性設計」の観点から最適であると判断。デバッグの不便さは Interceptor によるログ出力でカバーする。

## 6. Consequences (結果とトレードオフ)
- **Positive (+)**: スキーマ駆動開発により、API定義の変更が自動的に全リポジトリに伝播する（保守性の向上）。
- **Negative (-)**: gRPC の学習コストおよび、Webフロントエンド向けのプロキシ構築コストが発生する（トレードオフ）。
- **Residual Risk**: 外部システム（RESTのみ対応）と連携する際は、BFF側でプロトコル変換を行う必要がある。

## 7. More Information (補足)
- ADR-0002（BFFアーキテクチャの採用）とセットで実施。

---
"Structure over Speed. Contract over Convention."
© 2026 Standard Architecture Blueprint. Managed by System Architect.
