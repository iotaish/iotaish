# ishp@ctrin

情報工学科（CS）専攻。
数理モデルの厳密な閉形式実装、宣言的ルールによる開発者向け CLI ツール、および多段階の型変換を排したソフトウェア設計（スペードアーキテクチャ）を軸に開発を行っています。

## 目次 <!-- omit in toc -->

- [1. 主要プロジェクト][主要プロジェクト]
   - [1.1. プロトコル・数理シミュレーション][プロトコル・数理シミュレーション]
   - [1.2. 開発者ツール・ワークフロー自動化][開発者ツール・ワークフロー自動化]
   - [1.3. コミュニティ・基盤運用][コミュニティ・基盤運用]
- [2. 設計原則と技術スタック][設計原則と技術スタック]

## 1. 主要プロジェクト

### 1.1. プロトコル・数理シミュレーション

1. **[`dynaflux`][repo-dynaflux]** — Autonomous Verifiable Thermostatic Currency
   - 2つの時間スケールの指数減衰状態（`late` / `early`）により通貨発行量と移転税率を自律制御する $O(1)$ サーモスタット暗号資産プロトコルです。
   - 区間縮小つきパデ型有理関数近似による減衰計算、微分方程式の厳密積分による**完全な分割不変性（Path-Independent Split-Invariance）**、および `stateHash` 監査チェーンを備え、Ethereum Sepolia と Cloudflare Workers（Discord Bot）を直結してサーバーレスで稼働します。
1. **[`discord-casino-bot`][repo-casino]** — ペリカ経済圏・ミニゲーム & 金融シミュレータ Bot
   - サーバー別独立通貨「ペリカ」を基軸とした Discord 向け経済・ゲーム基盤です。
   - チンチロ・パチンコ・ブラックジャック等の遊技に加え、全サーバー共通価格で推移するトークンの現物・空売り取引、元本保証債とデフォルト確率を持つジャンク債、および日割り利息つきの P2P 貸付市場を実装しています。

### 1.2. 開発者ツール・ワークフロー自動化

1. **[`zipdir`][repo-zipdir]** — 宣言的ルールに基づくディレクトリ・パッケージング CLI
   - `.gitignore` 風の直感的なルール記法（`.zipignore`）により、`.git/` やビルド中間生成物（`.aux`, `.log` 等）を一括除外しつつ、必要な成果物（`out/report.pdf` 等）だけを救出・再配置・リネームして ZIP 化する Python 製 CLI ツールです。
   - 4階層カスケードのルール優先度解決、`--explain` による評価診断、および容量上限・空アーカイブ防止ガードを備えています。
1. **[`karabiner-json-generator`][repo-karabiner]** — Karabiner-Elements 設定ジェネレータ
   - 冗長な JSON ボイラープレートを排し、簡潔な YAML 定義から macOS Karabiner-Elements 用の `complex_modifications` ルールを生成するツールです。

### 1.3. コミュニティ・基盤運用

1. **[`cit-cs-hub`][org-cit-cs-hub]** — 千葉工業大学 情報工学科コミュニティ Organization
   - 講義知見の体系的アーカイブ、Fork & PR による課題コードの相互ピアレビュー、および GitHub Rulesets と Verified 署名を組み合わせた実践的な開発ガバナンス基盤を設計・運用しています。

## 2. 設計原則と技術スタック

1. **アーキテクチャと仕様記述**
   - **スペードアーキテクチャ (Spade Architecture)**: 入力事実の最小定義（Tip / 切っ先）、関係・グラフによる正規空間（Wings / 翼）、SQL・CSS 等による宣言的集約（Handle / 柄）、および出力射影（Base / 裾）の4層で責務を分離し、中間の冗長なデータ構造変換を排除します。
   - **3本柱の仕様書体系**: 課題の再帰的分解ツリー（`breakdown/`）、実装・思考・ドメインの衛生規律（`hygiene/`）、および運用手順（`procedures/`）によって「Why & Intent」を単一情報源（SSOT）として管理します。
1. **主要技術スタック**
   - **Languages**: Python, TypeScript / JavaScript, Solidity, C, Shell, LaTeX
   - **Runtime & Tooling**: uv, Ruff, Pyright, pytest, Deno, Cloudflare Workers, Git / GitHub CLI
   - **Data & Libraries**: Polars, DuckDB, Pydantic, FastAPI, Typer, discord.py

[主要プロジェクト]: #1-主要プロジェクト
[プロトコル・数理シミュレーション]: #11-プロトコル数理シミュレーション
[開発者ツール・ワークフロー自動化]: #12-開発者ツールワークフロー自動化
[コミュニティ・基盤運用]: #13-コミュニティ基盤運用
[設計原則と技術スタック]: #2-設計原則と技術スタック
[repo-dynaflux]: https://github.com/iotaish/dynaflux
[repo-casino]: https://github.com/iotaish/discord-casino-bot
[repo-zipdir]: https://github.com/iotaish/zipdir
[repo-karabiner]: https://github.com/iotaish/karabiner-json-generator
[org-cit-cs-hub]: https://github.com/cit-cs-hub
