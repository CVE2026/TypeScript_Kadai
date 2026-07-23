# オセロゲーム

ブラウザで遊べるオセロ（リバーシ）ゲームです。TypeScriptで実装し、コンパイルしたJavaScriptをブラウザで動作させています。

## 使用技術

- TypeScript
- HTML / CSS
- JavaScript（TypeScriptからコンパイル）

## 遊び方

1. 黒番からスタートし、石を置ける（ひっくり返せる）マスが黄色でハイライトされます。
2. ハイライトされたマスをクリックすると石を置き、相手の石をひっくり返します。
3. 置ける場所がない場合は「パスする」ボタンで手番を交代できます。
4. 盤面が埋まったら結果（黒/白の石数と勝敗）が表示されます。

## セットアップ・実行方法

TypeScriptはブラウザで直接実行できないため、事前にJavaScriptへコンパイルする必要があります。

```bash
# TypeScriptをインストールしていない場合
npm install -g typescript

# main.ts を main.js にコンパイル
npx tsc main.ts --target ES2017 --lib DOM,ES2017
```

コンパイル後、`index.html` をブラウザで開くとプレイできます。

## ファイル構成

```
.
├── index.html   # HTML本体
├── style.css    # スタイル
├── main.ts      # ゲームロジック（TypeScript／編集対象）
└── main.js      # main.tsのコンパイル結果（ブラウザが実際に読み込むファイル）
```

## 実装のポイント

- `StoneState`（石の状態）、`Color`（手番の色）を型として定義し、状態管理を型安全にしている
- `TurnManager` / `ReversiLogic` / `Board` / `Game` にクラスを分割し、責務を分離
- 8方向探索によるひっくり返せる石の判定ロジック（`ReversiLogic.getReversibleStones`）
