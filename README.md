# Atena Studio

名簿（CSV）から、宛名ラベル・QR付き受講票・名札・見積書などの個別書類をブラウザだけでまとめて作成するツールです。サーバー不要・登録不要・データはブラウザの外に送信されません。

**[今すぐ試す →](https://nekoai-lab.github.io/atena-studio/)**　|　**[使い方・機能紹介](https://nekoai-lab.github.io/atena-studio/about.html)**

## できること

- **21種類のテンプレート**（宛名ラベル・受講票・名札・会員証 など）から選ぶか、ゼロから自由に帳票を設計。うち見積書／発注書／納品書／受領書／請求書／領収書の6種は有料プラン限定（理由は下記「今後の展開」参照）
- **CSV読み込み、または表への直接入力**で名簿を用意（スプレッドシートからの貼り付けにも対応）
- 文字・QRコード・ロゴ・表・枠線を**ドラッグで配置**、配色・書体はプリセットから一括変更
- 自社情報（会社名・住所・連絡先・ロゴ）を登録しておけば、対応するテンプレートに**自動で差し込み**
- 名簿の**差分確認・過去バージョンへの復元**（IndexedDB保存）
- 検品用CSV出力、QRリンクへのUTMパラメータ自動付与
- レイアウトを**マイテンプレート**として保存し、次回から呼び出し

機能の詳細は [about.html](https://nekoai-lab.github.io/atena-studio/about.html)（使い方・機能紹介ページ）を参照してください。

## 利用方法

[https://nekoai-lab.github.io/atena-studio/](https://nekoai-lab.github.io/atena-studio/) にアクセスするだけで使えます。

## 技術構成

サーバーを持たない、ブラウザ完結型のクライアントサイドアプリケーションです。

- **PDF生成・解析**: [pdf-lib](https://pdf-lib.js.org/)（生成・編集）, [pdf.js](https://mozilla.github.io/pdf.js/)（背景PDFのプレビュー描画）, [fontkit](https://github.com/foliojs/fontkit)（カスタムフォント埋め込み）
- **QRコード**: [QRious](https://github.com/neocotic/qrious)
- **CSV解析**: [PapaParse](https://www.papaparse.com/)
- **ZIP出力**: [JSZip](https://stuk.github.io/jszip/)
- **スタイル**: [Tailwind CSS](https://tailwindcss.com/)
- 各ライブラリはCDNを優先し、CDNに到達できない環境（社内ネットワーク等）向けに `lib/` 配下へローカルフォールバックを同梱
- 名簿・自社情報・マイテンプレート・名簿バージョン履歴は、すべてブラウザの `localStorage` / `IndexedDB` に保存（サーバーには一切送信されません）

## プロジェクト構成

| パス | 内容 |
|---|---|
| `index.html` | アプリ本体（新規帳票デザイン・QR画像一括出力の2モード） |
| `about.html` | 使い方・機能紹介ページ |
| `assets/` | about.html掲載用の紹介画像・ロゴ |
| `lib/` | CDN到達不可時のローカルフォールバック用ライブラリ |
| `DESIGN.md` | 見た目の設計方針（構造・タイポグラフィ・シャドウ言語） |
| `ROADMAP.md` | 今後の拡張方針（無料版でどこまで実現するか／有料版で何を提供するか） |

## 今後の展開

現在は無料・サーバーレスの範囲でできることを突き詰めています。利用者が増えてきたら、複数人・複数端末での共有やサーバー連携が必要な機能（チーム利用、履歴のクラウド保管など）も有料版として検討する予定です。方向性の詳細は [ROADMAP.md](ROADMAP.md) を参照してください。

見積書・発注書・納品書・受領書・請求書・領収書の6テンプレートは、現状「CSV1行＝明細1行」までしか対応できておらず、実務では複数の商品・サービスを1枚にまとめたいケースがほとんどです。これをきちんと作るには、明細データの保存・編集を担うFirestoreのようなデータベースの構築・維持が必要になるため、無料のサーバーレス構成では提供が難しく、現在は有料プラン限定（テンプレートギャラリー上でロック表示）としています。

## ライセンス

All Rights Reserved. 著作権は [Marcrevix](https://marcrevix.com/) に帰属します。詳細は [LICENSE](LICENSE) を参照してください。カスタマイズのご相談は [こちら](https://marcrevix.com/contact/) から承っています。
