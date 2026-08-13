# ALifeCoreStudio

**複雑系・人工生命モデリングのためのブラウザ開発・実行環境**（日本語版）

*[English README](../README.md) · [1-page project overview（English）](../OVERVIEW.md)*

**ABM**（エージェントベースモデリング）、**EVO**（進化計算）、**IEC**（対話型進化計算）の
3つのアプリからなります。

各アプリは**単一の HTML ファイルで自己完結**しています。インストールもビルドもサーバも不要で、
ダブルクリックすれば現代的なブラウザ（デスクトップ・モバイル問わず）で動きます。

生成AI（ChatGPT / Gemini / Claude などのクラウド、または LM Studio などのローカル LLM）に
コードを書いてもらい、貼り付けて実行するだけで、自分の興味あるモデルを動かせます。
プログラミングの知識がなくても始められます。

---

## このツールのねらい

複雑系や生命・社会システムを「創ることで理解する」構成論的アプローチは、
設計 → 実装 → 実行 → 可視化 → 分析 → 再び設計、というサイクルの反復として進みます。
従来はとりわけ**実装**がボトルネックでした。ALifeCoreStudio は、モデル構築・可視化・分析の
**枠組みを固定**し、生成AIには**モデルの本質的なロジックだけ**を作らせます。
作法が毎回そろうので、AIが返したコードはそのままスライダーとグラフを備えた
動くモデルとして実行できます。

---

## はじめかた

1. このリポジトリをダウンロード（または `git clone`）します。

   ```bash
   git clone https://github.com/reijiszk/ALifeCoreStudio.git
   ```

2. 使いたいアプリの HTML ファイルを **ダブルクリックしてブラウザで開く**だけです。
3. 初めての方は、対応する「はじめてガイド」を先に開くのがおすすめです。

**動作環境:** 現代的なブラウザ（Chrome / Firefox / Safari / Edge）。インストール・依存関係・
サーバは不要で、モデルを動かすだけならインターネット接続も要りません。

> 💡 一部の機能（コードの実行＝`new Function`、AI 生成の通信）は、ページの提供環境に
> 制限の強い Content Security Policy が付いていると動きません。うまく動かない場合は、
> HTML を**通常のブラウザで直接（`file://`）開く**か、簡易サーバ（例 `python3 -m http.server`）で
> 配信してください。

---

## このフォルダの内容

すべて **v1.0** に統一されています。

| ファイル | 説明 |
|---|---|
| `ABM_Studio_ja.html` | **ABM Studio** — エージェントベースモデル（群れ・感染・住み分け 等） |
| `Evo_Studio_ja.html` | **EVO Studio** — 進化計算（遺伝的アルゴリズム、仮想生物の進化 等） |
| `IEC_Studio_ja.html` | **IEC Studio** — 対話型進化計算（あなたが「好み」で形を進化させる） |
| `ABM_Studio_FirstSteps_ja.html` | ABM Studio のはじめてガイド |
| `Evo_Studio_FirstSteps_ja.html` | EVO Studio のはじめてガイド |
| `IEC_Studio_FirstSteps_ja.html` | IEC Studio のはじめてガイド |
| `ABM_Studio_Manual_ja.html` | ABM Studio 詳細マニュアル（上級） |
| `Evo_Studio_Manual_ja.html` | EVO Studio 詳細マニュアル（上級） |
| `IEC_Studio_Manual_ja.html` | IEC Studio 詳細マニュアル（上級） |

入口ページ **`index.html`**（全アプリ・全ドキュメントへのリンク集）、
実験データ再生ビュワー **`ALifeCoreStudio_Viewer.html`**、`LICENSE` は、
リポジトリ直下（[`../`](../)）にあります。ビュワーは日英どちらのアプリの ZIP でも読み込めます
（画面表記は英日併記）。

---

## 生成AI でモデルを作る・改変する・理解する

各アプリのコードバーには次の機能があります。

- **✏️ 改変プロンプト / ✨ 新規作成プロンプト** … 仕様込みのプロンプトをクリップボードにコピー。
  ChatGPT / Gemini / Claude などに貼り付けて使えます。返答は「**貼り付けて適用**」の1操作で
  動作中のモデルへ反映できます。
- **📖 説明プロンプト** … 現在のモデルが何をしているかを、平易な言葉と疑似コードで
  説明してもらえます。JavaScript を読まなくても理解できます。
- **🐍 Python変換プロンプト**（ABM / EVO）… 現在のモデルを、同等で自己完結した
  Python（`matplotlib`）スクリプトへ変換します。
- **🤖 AI生成** … OpenAI 互換 API に直接つないで生成し、結果を自動でコード欄に挿入。
  ローカル（LM Studio など）でもクラウドでも使えます。

生成・実行・改変・説明がすべて同じページ上で完結するので、モデリングのサイクルを
そのまま回し続けられます。接続先の例や CORS の設定など詳しい使い方は、
各「はじめてガイド」の該当節を参照してください。

---

## ビルトインモデル

- **ABM Studio**: 初等セルオートマトン（ECA）、ライフゲーム、住み分け（分居）、群れ（フロッキング）、
  アリのフェロモン、空間囚人のジレンマ、SIR 感染症、ソーシャル・パーティクル・スウォーム（SPS）
- **EVO Studio**: ビット列 GA（関数最適化）、質点バネ生物、ソフトボディ生物、ナップザック問題、巡回セールスマン問題（TSP）
- **IEC Studio**: 枝分かれ図形、群れ（アニメ）、顔の進化、ステンドグラス、数式アート、仮想生物（ソフトボディ）、音の進化

各モデルが題材にしている原典は、各「はじめてガイド」末尾の **「参考文献・出典」** にまとめています。

---

## 実験データの記録・再生

各アプリの **「📦 一式DL」** で、初期化以降のデータを ZIP でまとめて書き出せます
（`model.js`・パラメータ・実験設定・乱数シード・グラフ CSV・全体の JSON）。
あとで解析・再現できるよう、次の2つの仕組みで**各ステップ・世代の様子を再現**できます。

- **方式A（決定的シード）**: 実行中の乱数はエンジンがシードで固定し、そのシードを記録します。
  `model.js` ＋ 設定 ＋ シードから同じ実行を再現できます（改変・新規作成したモデルでも同様）。
- **方式B（状態の記録）**: ABM / EVO は「**状態を記録**」で各ステップ・世代の状態を
  `frames.jsonl` に保存します（IEC は各世代の9個体を常に記録）。アプリ内のタイムラインも
  この記録を再生するので、実行中に気づいた現象へいつでも戻れます。**PCでは既定でオン、
  メモリの余裕が少ないスマートフォン・タブレットでは既定でオフ**です。いつでも切り替えられます。

書き出した ZIP を、リポジトリ直下の **`ALifeCoreStudio_Viewer.html`** にドロップすると、
記録した各ステップ・世代を、そのモデル自身の描画コードで**タイムライン再生**できます。
組み込みモデルだけでなく、生成AI で改変・新規作成したモデルでも動きます。

---

## 開発体制について

ALifeCoreStudio は著者1人で開発しています。MIT License のもとで誰でも自由に利用・改変・
フォークできますが、現時点では Pull Request は受け付けていません。各アプリが数千行の
単一 HTML ファイルであり、外部からの差分をマージする形に向いていないためです。

不具合の報告や質問は [Issues](https://github.com/reijiszk/ALifeCoreStudio/issues) へお寄せ
ください。フォークして独自に発展させていただくのも歓迎です。

---

## ライセンス

本ソフトウェアは **MIT License** で配布されます（[`../LICENSE`](../LICENSE) を参照）。

---

## 引用

本ツールに含まれる **ソーシャル・パーティクル・スウォーム（SPS）モデル**を研究等で参照する場合は、
次の論文を引用してください。

> Nishimoto, K., Suzuki, R., & Arita, T. (2023).
> Social Particle Swarm model for investigating the complex dynamics of social relationships.
> *Psychologia*, 65(2), 185–210. https://doi.org/10.2117/psysoc.2023-B039

---

## 授業・セミナーでのご利用について

授業やセミナー、ワークショップで ALifeCoreStudio をお使いいただける場合、ご一報いただけると
嬉しく思います（<reiji@nagoya-u.jp>）。**ライセンス上の条件ではなく、あくまでお願いです。**
どのように使われているかがわかると改善の方向を判断する助けになりますし、どんなモデルが
作られたかをうかがえるのは単純に楽しみでもあります。

---

## 謝辞

本ツールは [NetLogo](https://www.netlogo.org/)（Wilensky, U., 1999, Center for
Connected Learning and Computer-Based Modeling, Northwestern University）から大きな影響を
受けています。著者はこれまで NetLogo を自身の研究や授業に活用しており、その経験が本ツールの
着想と設計の土台になっています。ここに記して深く感謝します。なお、NetLogo Models Library にも
同種の題材があるモデルもありますが、ABM Studio の各モデルは同じ古典的アルゴリズムを
独立に実装したものです。

ソフトボディ（ボクセル仮想生物）モデルは、**Evolution Gym** の「ボクセルでソフトロボットを
進化させる」という着想から発想を得た独立実装で、物理モデル（位置ベース動力学）を含めて
独自に実装しています。

- Evolution Gym: Bhatia, J., Jackson, H., Tian, Y., Xu, J., & Matusik, W. (2021).
  *Evolution Gym: A Large-Scale Benchmark for Evolving Soft Robots.* NeurIPS 2021.
  https://github.com/EvolutionGym/evogym

本アプリ自体のコードおよびドキュメントは、[Claude Code](https://claude.com/claude-code) を
活用して構成したものです。

書体（IBM Plex Mono / Syne / Noto Sans JP, すべて SIL OFL 1.1）は同梱しておらず、
実行時に Google Fonts から読み込まれます。

---

## 作者

Reiji Suzuki（鈴木麗璽、名古屋大学） — <reiji@nagoya-u.jp>
