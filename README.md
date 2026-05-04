# Architecture Standards & Guidelines (ASG)

> **"Total Governance from Requirement to Quality Assurance."**

本リポジトリは、Standard Architecture Blueprint (SAB) プロジェクトにおける、上流工程（要件定義・設計）から下流工程（実装・テスト）、および運用基盤に至るすべての「技術標準」と「意思決定」を統治する中央拠点である。

## 📌 目的
本プロジェクトに従事するすべての開発者は、本リポジトリで定義された制約事項（Constraints）を遵守し、13のリポジトリ全体で「論理的整合性」と「品質の均一化」を担保しなければならない。

## 🏛️ ディレクトリ構成と管理資産

各ディレクトリは、システム開発ライフサイクル（SDLC）における「基準（Baseline）」として機能し、13のリポジトリ全体の整合性を統治する。

### 1. Management & Processes
**【役割：軍紀】開発工程の標準化**
- AP試験の「システム開発ライフサイクル（SDLC）」に基づく工程管理。
- **Requirement Definition**: 機能・非機能要件（RASIS）の抽出ルール。
- **Process Guideline**: 要件定義からリリースに至る承認フロー（変更管理）。
- **Document Rules**: Mermaid図解（クラス図、シーケンス図、ER図）の標準記法。
- **目的**: 開発プロセスの透明性を確保し、プロジェクトマネジメントの属人性を排除する。

### 2. ADR (Architecture Decision Records)
**【役割：参謀記録】技術選定の論理的根拠**
- 技術選定の論理的根拠を管理。
- 決定に至る背景、代替案との比較、トレードオフの記録（MADR形式を採用）。
- **目的**: 「なぜその設計になったか」という意思決定の追跡可能性（Traceability）を担保する。

### 3. Design Guidelines
**【役割：作戦定石】共通設計の規約**
- **Domain Modeling**: 境界付けられたコンテキストとデータ整合性方針（整合性制約）。
- **Interface Design**: RESTful API規約および共通レスポンス構造（ApiResponse）。
- **Architecture Patterns**: SoE/SoR/SoI の分離と依存方向の定義。
- **目的**: マイクロサービス間の通信およびデータ構造の整合性を維持し、全体最適を図る。

### 4. Engineering Standards
**【役割：戦技】実装品質の「正解」定義**
- 実装工程（下流）におけるコーディング規約。
- **Coding Standard**: 命名規約、例外ハンドリング（BaseException）、ログ出力規約。
- **Design Patterns**: 依存性の注入（DI）、戦略パターン等の推奨適用例。
- **Security Implementation**: JWT検証、入力バリデーション、秘密情報管理。
- **目的**: 誰が書いても「帝国標準」の品質となるよう、コードレベルで制約を課す。

### 5. Quality Assurance & Testing
**【役割：検閲】品質保証の合否基準**
- 品質保証工程の合否基準。
- **Test Strategy**: 単体テスト（C0/C1網羅率）、結合テスト、回帰テストの範囲。
- **Quality Gates**: PR承認に必要なテストパス条件および静的解析（Lint/Checkstyle）基準。
- **Evidence Standards**: 検証結果の記録（トレーサビリティ）に関する証跡標準。
- **目的**: 出荷される成果物の品質を定量的・客観的に証明し、監査に耐えうる状態にする。

### 6. Templates & Artifacts
**【役割：軍需物資】再利用可能な共通資産**
- **Artifact Templates**: 要件定義書、基本設計書、詳細設計書のMarkdown雛形。
- **Code Scaffolding**: 各種リポジトリ（Backend/Frontend/Library）の初期構造。
- **目的**: 構築コストを最小化し、迅速な展開（Rapid Deployment）と構造の統一を実現する。

### 📂 リポジトリ実体構造 (Physical Structure)
```
standards/
├── processes/                 # 1. Management & Processes
│   ├── requirement-rule.md    # 要件定義（機能・非機能・RASIS）
│   ├── model-driven-rule.md   # Mermaid標準記法
│   └── release-process.md     # 承認フロー・変更管理
├── adr/                       # 2. ADR (Architecture Decision Records)
│   ├── 0001-template.md       # MADR形式の雛形
│   └── [YYYYMMDD]-decision.md # 決定記録の蓄積
├── design/                    # 3. Design Guidelines
│   ├── domain-modeling.md     # DDD・データ整合性
│   ├── api-standard.md        # ApiResponse・REST規約
│   └── architecture-patterns.md# SoE/SoR/SoI分離ルール
├── engineering/               # 4. Engineering Standards
│   ├── coding-standard.md     # 命名・BaseException・ログ
│   ├── design-patterns.md     # DI・共通パターン
│   └── security-standard.md   # JWT・秘密情報管理
├── testing/                   # 5. Quality Assurance & Testing
│   ├── test-strategy.md       # C0/C1網羅率・テスト範囲
│   ├── quality-gates.md       # PR承認基準・静的解析ルール
│   └── evidence-standard.md   # 証跡（トレーサビリティ）標準
├── templates/                 # 6. Templates & Artifacts
│   ├── docs/                  # RD/FD/DDのMarkdown雛形
│   └── code/                  # 各言語リポジトリの初期構造
└── README.md                  # 本リポジトリのマニュアル（全体統治）
```

## 📝 開発プロセス（SDLC）の実践

1. **定義**: `templates/docs/` の雛形を用いて要件を具体化し、機能・非機能の両面を定義する。
2. **審議**: 重要な技術決定は `adr/` で提案し、トレードオフを論理的に評価する。
3. **構築**: `templates/code/` を継承し、`engineering/` の規約を「制約」としてコードを記述する。
4. **検証**: `testing/` の基準に基づき品質を証明し、要件に対する追跡可能性（Traceability）を確保する。

## ⚖️ 準拠性 (Compliance)
- **Total Optimization**: 局所的な最適化よりも、本リポジトリが定める全体最適を優先せよ。
- **Drift Prevention**: 実装とドキュメントに乖離が生じた場合、速やかに本規約またはADRを更新し、情報の鮮度を維持せよ。

---
"Governance through Logical Rigor."
© 2026 Standard Architecture Blueprint. Managed by System Architect.
