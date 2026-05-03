# API Design Guidelines (Web API 標準)

## 📌 概要
システム間およびレイヤ間の通信は、原則として REST (Representational State Transfer) の原則に従う。

## 🛠️ 基本原則
1. **リソースベース**: URLには名詞を用い、操作（動詞）は HTTP メソッド（GET, POST, PUT, DELETE）で表現する。
   - `GET /users` (一覧取得)
   - `POST /users` (作成)
2. **ステートレス**: サーバー側にクライアントの状態を保持せず、リクエストごとに認証トークン（JWT）を検証する。

## 📋 共通レスポンス形式
すべてのAPIは、エラー時も含め統一されたエンベロープ形式で返却する。
```json
{
  "status": "success | error",
  "data": { ... },
  "error": {
    "code": "ERROR_CODE",
    "message": "Human readable message"
  },
  "timestamp": "2026-05-03T16:00:00Z"
}
