# GPU 以外の選択肢！開発チームが徹底解説、効率的な AI 基盤の作り方

## 日時
2025/6/25 16:50

## 発表者
常世 大史

アマゾン ウェブ サービス ジャパン合同会社
Annapurna Labs, ML SA

## abstract
AWS では低コストで高性能、電力効率の高い AI 基盤を実現するためのインフラ技術として、AI アクセラレータチップ AWS Trainium、Inferentia を自社開発してきました。本セッションでは、昨年末に一般公開開始した最新の Trainium2 搭載 Amazon EC2 Trn2 インスタンスから AWS Trn2 UltraServers、AWS 世界最大規模の学習環境となる Project Rainier まで、AWS のカスタムシリコン戦略の全容をご紹介します。セッション後半では、大規模言語モデル Claude を提供している Anthropic 社や、Alexa、Rufus といった Amazon の各種サービスなど、AWS Trainium/Inferentia を活用頂いているお客様の事例をご紹介するとともに、より実践的な内容として、日本語 OSS モデルを利用した推論サーバーの構築手順と TIPS について解説致します。本セッションは、大規模言語モデルの学習・推論環境の構築を検討されている方々、特にインフラコストの最適化に課題をお持ちの方に役立つ内容となっています。

## 概要メモ
- アンナプルナラボ
  - AWSが買収した半導体会社がもと
  - 半導体開発
  - 10年前買収
- コスト最適化には半導体開発が不可欠
- Trainium：GPU以外の機械学習推論？
- Inferentia2, Trainium：向きは違うが、内部では同じコアプロセッサ（Nuronコア）を利用している
- 1600Gpbsってすごいな……
- シストリックアレイ構造
  - 隣接する演算ユニットに渡していく
  - データの受け渡しは局所的に行われる→演算効率を最大限に高めている
- Inferentia2
  - 内部はTraniumとほぼ同じ
  - ネットワーク接続を簡素化→低コスト推論を実現
  - EFAは搭載していない
- Trainium2
  - 3200Gpbs!?
  - もう何がなんだかw
  - チップ内のコア数が2->8
  - Structured Spacity
    - 使用メモリを圧縮して演算することができる
- 電圧レギュレータ
  - 近ければ近いほどいい
- 機械学習のワークロードは即座に需要が発生する
- Tranium2を入れたサーバー
  - シンプルなデザインでケーブルが一歳ない
  - 空冷水冷どちらでも対応
- UltraServers
  - 名前、かっこいいなw
- 独自設計＝使い勝手が悪い？
- 国内外の事例紹介＆実際にサーバ構築
- Tranium活用事例
  - AlexaなどAmazonサービス
    - Rufus
  - Anthropic
    - Claude 3.5 haikuはTranium2を使用している
- サーバの構築手順
- Nuron SDK
- NxD：PyTorch上で分散推論向けのライブラリ
- NeuronSDK
  - EKSなどAWS各種サービス＋サードパーティ製と綿密に連携可能
- PyTorch上でNxDを使用する環境を選択
- SageMaker
  - 推論：SageMaker Studio
- HuggingFace TGI：HuggingFace上のモデルを簡単にデプロイできる
  - 表示されたスクリプトをコピーして実行するだけ！
  - コンパイル済みのキャッシュがあれば、デプロイ時間を短縮可能
- 