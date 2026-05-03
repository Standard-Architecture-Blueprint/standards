# Frontend Angular Project Template

## 📌 概要
本プロジェクトは、複数のサービス群におけるフロントエンド開発の標準雛形である。応用情報技術者試験（AP）の「ヒューマンインタフェース設計」および「Webシステム設計」の原則に基づき、保守性、アクセシビリティ、およびUIの一貫性を最大化したモジュール構造を採用している。

## 📂 ディレクトリ構造と役割
AP試験の「モジュール独立性（高凝集・低結合）」およびAngularのベストプラクティス（LIFT原則）に基づき、以下の階層構成を厳守すること。
```text
src/app/
├── core/             # 【Core Module】
│   │                 # アプリ全体で唯一のインスタンス。全画面共通の基盤。
│   ├── auth/         # 認証ガード（AuthGuard）、ログイン状態管理。
│   ├── interceptors/ # HTTP通信の共通割込（トークン付与、エラー一括処理）。
│   └── services/     # アプリ全体のライフサイクルを管理するシングルトンサービス。
│
├── shared/           # 【Shared Module】
│   │                 # 複数の機能モジュールで再利用するステートレスな部品。
│   ├── components/   # ボタン、ダイアログ、ローディング表示などのUI部品。
│   ├── directives/   # 権限制御や入力制限などのカスタムディレクティブ。
│   └── pipes/        # 日付整形、通貨表示などの共通変換処理。
│
├── features/         # 【Feature Modules】
│   │                 # 業務ドメインごとの機能単位。Lazy Loading（遅延ロード）対象。
│   └── user/         # （例：ユーザー管理機能）
│       ├── components/ # 機能固有のコンポーネント。
│       └── pages/      # ルーティングに対応する画面全体のコンポーネント。
│
├── data/             # 【Data Layer】
│   │                 # 外部連携およびデータ構造定義。UI層からロジックを分離。
│   ├── models/       # APIレスポンス等の型定義 (interface / type)。
│   └── services/     # HttpClientを用いたAPI通信の具象クラス。
│
└── styles/           # 【Presentation Layer】
    ├── abstracts/    # Tailwind CSSのカスタム変数やMixin。
    └── themes/       # ブランドカラー、ダークモード等のデザインシステム定義。
```
## 🛠️ 技術スタック（デファクトスタンダード）
AP試験の「標準化」および「Webアプリケーション」に基づき選定。

| カテゴリ | 選定技術 | 理由・AP試験との関連 |
|:---|:---|:---|
| **Framework** | Angular 17+ | 厳格な構造化による**大規模開発**の統制。 |
| **Language** | TypeScript | 静的型付けによる**信頼性**と保守性の向上。 |
| **Styling** | Tailwind CSS | **デザインシステム**のコード化（一貫性の担保）。 |
| **State Mgmt** | RxJS | **非同期処理（Observerパターン）**の標準実装。 |
| **Form** | Reactive Forms | 複雑なバリデーションの論理的制御。 |
| **Lint/Format** | ESLint / Prettier | 静的解析によるコード品質の均一化。 |

## 📐 実装規約 (Frontend Rules)
AP試験の「ソフトウェア品質特性（使用性、保守性）」を確保するための5原則。

1. **コンポ―ネントの責務分離**: 
   - プレゼンテーショナル（表示専用）とコンテナ（データ処理用）を分けること。
2. **型の厳格運用**: 
   - `any` 型の使用を原則禁止し、APIレスポンス等は必ず `data/models` で型を定義すること。
3. **HTTPインターセプターの活用**: 
   - 401(認証切れ)や500エラーの共通処理は `core/interceptors` で一括ハンドリングすること。
4. **アクセシビリティ (A11y)**: 
   - セマンティックなHTMLタグを使用し、適切なARIA属性を付与すること。
5. **パフォーマンス最適化**: 
   - `features/` 配下のモジュールは必ず遅延ロード（Lazy Loading）を適用すること。

## 🚀 セットアップ手順
1. **依存関係のインストール**:
   ```bash
   npm install
2. **ローカル開発サーバーの起動**:
   ```bash
   npm start
3. **ビルド（本番環境用）**:
   ```bash
   npm run build --prod
## 🧪 テスト・品質管理
AP試験の「テスト工程」に基づき、品質を担保する。

- **Unit Test**: 
  - Jasmine/Karmaを用い、ServiceのロジックやPipeの変換結果を網羅する。
- **E2E Test**: 
  - Playwright等を用い、主要なユーザージャーニー（正常系）を自動検証する。

---
© 2026 Standard Architecture Blueprint.
