### 1. 開催概要

| 項目 | 内容 |
| :--- | :---------- |
| **セッション名** | AWS Amplify で加速する生成 AI アプリケーション開発 (AWS-16) |
| **日時** | 2025年6月25日 14:50 |
| **発表者** | 稲田 大陸 氏（アマゾン ウェブ サービス ジャパン合同会社 技術統括本部 エンタープライズ技術本部 自動車・製造グループ ソリューションアーキテクト）|
| **概要** | AWSの次世代開発プラットフォーム「AWS Amplify Gen 2」と、生成AI開発アシスタント「Amazon Q Developer」を組み合わせ、AIアプリケーション開発をいかに高速化・効率化できるかを解説したセッションである。TypeScriptによるコードファーストな開発、開発者ごとのサンドボックス環境、そして「Amplify AI Kit」を用いた生成AI機能の簡単な実装方法が、デモンストレーションを交えて紹介された。 |

### 2. 主要なポイント

#### **1. AWS Amplify Gen 2による開発体験の変革**
Amplifyの次世代バージョンであるGen 2は、開発体験を大幅に向上させるものであった。従来のCLIベースのGen 1から進化し、AWS CDKを基盤としたコードファーストなアプローチを採用している。

* **フルスタックTypeScript開発:**
    バックエンドのリソース（データモデル、認証、ストレージ、関数など）とフロントエンドのコードを、すべてTypeScriptで一元的に記述できる。これにより、エンドツーエンドでの型安全性が確保され、開発効率とコードの品質が向上する。

* **開発者ごとのクラウドサンドボックス:**
    `git push`などをトリガーに、開発者ごと、あるいはブランチごとに独立したバックエンド環境をAWS上に自動で構築できる。これにより、チーム開発における環境の競合や依存関係の問題を解消し、各開発者が独立して安全に開発・テストを進めることが可能となる。

* **認証機能の簡易実装 (Amplify Auth):**
    認証が必要なフロントエンドコンポーネントを`<Authenticator>`で囲むだけで、サインイン、サインアップ等のUIとバックエンドロジック一式を数行のコードで実装できる。これにより、複雑な認証フローの構築にかかる手間が大幅に削減される。

#### **2. Amplify AI Kitによる生成AI機能の高速実装**
フルスタックアプリケーションに対し、生成AI機能を爆速で追加するためのキットであり、本セッションの核心部分であった。Amazon Bedrockを利用した機能を、すべてTypeScriptのコードで定義できる。

* **シンプルなコードによるAI機能定義:**
    デモンストレーションでは、レビュー投稿を要約する機能が紹介された。バックエンド側では、使用する基盤モデル（例: Claude 3 Haiku）とプロンプトを数行のTypeScriptコードで定義するだけでAI要約機能が完成する。フロントエンド側は、提供されている専用のフック（`useAIGeneration`）を呼び出すだけで、この機能を利用できる。

* **高度な会話型UIの高速構築:**
    物件チャットボットのデモでは、画像のアップロードや対話形式での検索といった高度な機能が紹介された。バックエンドは`conversation()`を定義するわずか十数行のコードで実装され、フロントエンドはプリセットされた`<AIConversation>`コンポーネントを配置するだけで、ストリーミングレスポンスに対応したインタラクティブなチャットUIを構築可能である。

* **RAG (Retrieval-Augmented Generation) アーキテクチャの容易な活用:**
    Amplify AI Kitは、`Knowledge Bases for Amazon Bedrock`とのシームレスな連携をサポートしている。これにより、自社のドキュメントやデータベースといった独自のデータソースに基づいた回答を生成するRAGアーキテクチャを容易にアプリケーションに組み込むことができ、より実用的なAI機能を実現できる。

#### **3. Amazon Q Developerによるインテリジェントな開発支援**
セッションでは、Amplify Gen 2とAmazon Q Developerを組み合わせることで、開発者体験がさらに向上することが示された。

* **自然言語によるコード生成と修正:**
    Amazon Q Developerのチャット機能を使うことで、「このコンポーネントを日本語化して」といった自然言語の指示に基づき、コードの生成や修正、リファクタリングが可能である。これにより、専門外のフレームワーク（例: React）を扱う場合でも、スムーズに開発を進めることができる。

* **開発ライフサイクル全体のサポート:**
    コーディングだけでなく、デバッグ、テスト、技術的な調査など、開発のあらゆる場面でインテリジェントな支援を提供し、開発者全体の生産性を向上させる。
