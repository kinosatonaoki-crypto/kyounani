# 今日何着ていく？ 上富田版 🌤️

和歌山県上富田町向けの天気＆服装アドバイスアプリです。  
アプリを開くだけで、今日の天気・服装・持ち物・おすすめスポット・AIコメントが自動表示されます。

## 機能

- 🌤️ リアルタイム天気（Open-Meteo API / 無料・APIキー不要）
- 👕 気温・降水確率・風速に応じた服装アドバイス
- 🎒 持ち物リスト（傘・帽子・水分など）
- 🤖 AI による毎日変わるひとことコメント（Claude API）
- 📍 天気・気温に連動したおすすめスポット
- ☀️ 熱中症・洗濯・散歩・運動の指数（★5段階）
- 🌅 明日の服装と気温比較
- 📱 PWA 対応（ホーム画面に追加可能）
- 🌙 昼夜・天気で背景が自動変化

---

## ファイル構成

```
kamitonda-weather/
├── index.html          # メインアプリ（フロントエンド）
├── manifest.json       # PWA 設定
├── sw.js               # Service Worker（オフライン対応）
├── vercel.json         # Vercel デプロイ設定
├── .env.example        # 環境変数のテンプレート
├── .gitignore
├── icons/
│   ├── icon-192.png    # PWA アイコン
│   └── icon-512.png    # PWA アイコン（大）
└── api/
    └── comment.js      # Vercel Serverless Function（AIコメント生成）
```

---

## セットアップ

### 1. リポジトリをクローン

```bash
git clone https://github.com/あなたのユーザー名/kamitonda-weather.git
cd kamitonda-weather
```

### 2. Anthropic API キーを取得

1. [https://console.anthropic.com/](https://console.anthropic.com/) にアクセス
2. サインアップ／ログイン
3. 「API Keys」→「Create Key」でキーを発行
4. 発行されたキーをコピーしておく

> APIキーがなくても天気情報・服装アドバイスは表示されます。AIコメントのみ定型文になります。

---

## Vercel へのデプロイ（推奨）

### 方法 A：Vercel ダッシュボードから（かんたん）

1. [https://vercel.com/](https://vercel.com/) にログイン（GitHub アカウントで OK）
2. 「Add New Project」→ このリポジトリを選択
3. **Environment Variables** を設定：
   | 変数名 | 値 |
   |---|---|
   | `ANTHROPIC_API_KEY` | 取得した API キー |
4. 「Deploy」をクリック → 完了 🎉

### 方法 B：Vercel CLI から

```bash
# Vercel CLI をインストール
npm install -g vercel

# ログイン
vercel login

# デプロイ（初回）
vercel

# 環境変数を設定
vercel env add ANTHROPIC_API_KEY

# 本番デプロイ
vercel --prod
```

---

## GitHub へのプッシュ

```bash
# リポジトリを初期化（クローンではなく新規の場合）
git init
git add .
git commit -m "🌤️ 初回コミット：上富田お天気アプリ"

# GitHub にリポジトリを作成してからプッシュ
git remote add origin https://github.com/あなたのユーザー名/kamitonda-weather.git
git branch -M main
git push -u origin main
```

> GitHub にプッシュすると、Vercel と連携している場合は自動で再デプロイされます。

---

## ローカルで動作確認

Vercel CLI を使うとローカルでも Serverless Function を含めて動作確認できます。

```bash
# .env ファイルを作成（.gitignore に含まれているため Git にはコミットされません）
cp .env.example .env
# .env を開いて ANTHROPIC_API_KEY を設定

# ローカル起動
npx vercel dev
# → http://localhost:3000 でアクセス
```

---

## スマホのホーム画面に追加（PWA）

**iPhone（Safari）**
1. Safari でアプリの URL を開く
2. 画面下の「共有」ボタン（□↑）をタップ
3. 「ホーム画面に追加」をタップ

**Android（Chrome）**
1. Chrome でアプリの URL を開く
2. 右上メニュー（⋮）→「アプリをインストール」または「ホーム画面に追加」

---

## 使用 API・技術

| 項目 | 内容 |
|---|---|
| 天気データ | [Open-Meteo API](https://open-meteo.com/)（無料・APIキー不要） |
| AI コメント | [Anthropic Claude API](https://www.anthropic.com/)（claude-haiku） |
| デプロイ | [Vercel](https://vercel.com/) |
| フロント | HTML / CSS / Vanilla JS（フレームワーク不要） |
| バックエンド | Vercel Serverless Function（Node.js） |

---

## ライセンス

MIT
