# Operations & SRE Standards (運用保守・SRE標準)

## 📌 概要
本ディレクトリは、システムの可用性、信頼性、および保守性を継続的に維持するための「運用設計」を定義する。応用情報技術者試験（AP）の「サービスマネジメント」および「ITIL」のフレームワークに基づいた運用を実現する。

## 🎯 目的
1. **サービスレベルの維持**: SLA/SLOに基づき、ユーザーに約束した品質を担保する。
2. **インシデントの迅速な復旧**: 障害検知から復旧までの時間（MTTR）を最小化する。
3. **継続的改善**: 運用データを分析し、システムのボトルネックを排除する。

## 📋 運用ドキュメント一覧

| ファイル名 | 定義内容の要約 | 関連する知識体系 |
|:---|:---|:---|
| [monitoring-observability.md](./monitoring-observability.md) | 監視項目、ログ収集、トレーシング、アラート基準 | 可用性管理, ITIL |
| [incident-management.md](./incident-management.md) | 障害対応フロー、連絡体制、再発防止策 | 構成管理, インシデント管理 |
| [backup-recovery.md](./backup-recovery.md) | バックアップ頻度、リカバリ手順、RTO/RPO | 事業継続計画 (BCP) |
| [capacity-management.md](./capacity-management.md) | リソース監視、スケール戦略、コスト最適化 | キャパシティ管理 |

## 📐 運用の基本原則
- **Observability (観測可能性)**: 「何かが起きている」だけでなく「なぜ起きているか」を外部から把握可能にする。
- **Toil Reduction (苦役の削減)**: 繰り返しの手作業（トイル）を自動化し、エンジニアが価値創造に集中できる環境を作る。
- **Security in Ops**: 運用作業における特権アクセス管理（IAM）と操作ログの保存を徹底する。

---
© 2026 Standard Architecture Blueprint.
