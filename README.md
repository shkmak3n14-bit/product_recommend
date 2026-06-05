# product_recommend
📘 対話型商品レコメンド生成AIアプリ
生成AI（LLM）と RAG を活用し、ユーザーの要望に応じて商品をレコメンドする Web アプリです。
Streamlit を用いて構築しており、CSV の商品データと画像ファイルを元に、
「会話しながら商品をおすすめする AI アプリ」 を実現しています。

🚀 主な機能
● 対話形式での商品レコメンド
ユーザーがチャット欄に要望を入力すると、AI が最適な商品を検索し、画像付きで提案します。

● RAG（検索拡張生成）による高精度検索
　・BM25
　・OpenAI Embeddings
　・EnsembleRetriever（重み付き統合）
これらを組み合わせることで、
キーワード検索＋意味検索のハイブリッド検索 を実現しています。

● 商品情報の表示
　・商品名
　・価格
　・カテゴリ
　・メーカー
　・評価（レビュー数）
　・商品画像
　・商品説明
　・おすすめ対象ユーザー
　・商品ページへのリンク

🧩 アプリ構成
```bash
project/
├── main.py                # アプリのメイン処理
├── components.py          # 画面表示（UI）専用の関数
├── constants.py           # 固定値・設定の一元管理
├── initialize.py          # 初期化処理（ログ・RAG・セッション）
├── utils.py               # 形態素解析などの補助関数
├── data/
│   └── products.csv       # 商品データ（RAGのデータソース）
├── images/
│   ├── ai_icon.jpg
│   ├── user_icon.jpg
│   └── products/          # 商品画像（jpg）
│       └── xxx.jpg
└── logs/
    └── application.log    # ログファイル
```

🛠 使用技術
● 言語・フレームワーク
　・Python 3.x
　・Streamlit

● AI / RAG
　・LangChain
　・OpenAI Embeddings
　・ChromaDB
　・BM25Retriever
　・EnsembleRetriever

● 日本語処理
　・SudachiPy（形態素解析）

● ログ管理
　・TimedRotatingFileHandler による日次ログローテーション

📦 セットアップ方法
1. 必要ライブラリのインストール
```bash
pip install -r requirements_windows.txt
```
　（※ requirements_windows.txt は必要に応じて作成）

2. 環境変数の設定
　.env に OpenAI API キーを設定します。
```bash
OPENAI_API_KEY=your_api_key
```

4. アプリの起動
```bash
streamlit run main.py
```

📄 データ構造（products.csv）
CSV は以下のような形式を想定しています：
| id | name | price | category | maker | score | review_number | file_name | description | recommended_people |
|----|------|--------|----------|--------|--------|----------------|-----------|--------------|---------------------|
| 1  | サンプル商品 | 1980 | 家電 | メーカーA | 4.5 | 120 | sample.jpg | 〜説明〜 | 〜対象〜 |

商品画像は images/products/ に配置します。

🖼 表示例
　商品名
　価格
　カテゴリ
　メーカー
　評価（レビュー数）
　商品画像
　商品説明
　おすすめ対象ユーザー
　商品ページリンク

🧪 このアプリでできること
CSV と画像があれば、どんな商品データでもレコメンド可能
商品検索ツールとして利用可能
社内向け FAQ / ナレッジ検索にも応用可能
LLM を使った商品説明生成にも対応可能

📚 ライセンス
本プロジェクトは個人学習およびポートフォリオ公開を目的としています。
商用利用や再配布はご遠慮ください
