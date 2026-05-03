# Project Templates (プロジェクト雛形資産)

## 📌 概要
本ディレクトリは、新機能の開発や新規マイクロサービスの立ち上げを迅速化するためのスターターキットを管理する。すべてのテンプレートは、本リポジトリの `design/` および `engineering/` 規約を事前に適用済みである。

## 🎯 目的
1. **ボイラープレートの削減**: プロジェクト開始時の定型的な設定作業を排除する。
2. **規約の強制適用**: 意識せずとも標準化されたディレクトリ構成や命名規則に従えるようにする。
3. **学習コストの低減**: 13リポジトリのどこを担当しても、同じ構造でコードが書ける状態を作る。

## 📂 テンプレート一覧

| テンプレート名 | 用途 | 主要技術スタック |
|:---|:---|:---|
| [backend-spring-boot/](./backend-spring-boot) | SoRレイヤのAPI開発用 | Java 17, Spring Boot, Maven |
| [frontend-angular/](./frontend-angular) | SoEレイヤの画面開発用 | Angular, TypeScript, Tailwind CSS |
| [common-library/](./common-library) | 共通ロジック、ユーティリティ用 | Java (Jarファイルとして配布) |
| [github-actions/](./github-actions) | CI/CDパイプライン | YAML (GitHub Actions) |
| [adr-template.md](./docs/adr-template.md) | 新規ADR作成用 | Markdown |

## 🚀 使用方法
新規リポジトリを作成する際は、対象のテンプレートをベースに `git init` を行い、プロジェクト名やパッケージ名を一括置換して開始すること。

## ⚠️ メンテナンス方針
テンプレートは「生きた資産」である。`engineering/` や `ops/` の規約がアップデートされた際は、速やかにテンプレートにも反映し、常に最新の「正解」を保つこと。

---
© 2026 Standard Architecture Blueprint.
