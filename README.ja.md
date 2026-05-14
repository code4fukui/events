# events

Node.js互換の`EventEmitter`実装です。Deno、ブラウザ、Node.jsなどのモダンなJavaScript環境向けのESモジュールとして提供されています。

## 機能

- 標準的なNode.jsの`EventEmitter` API（`on`、`emit`、`once`など）を実装
- Deno、ブラウザ、Node.jsでネイティブに利用できるピュアESモジュール
- TypeScriptで記述されており、依存関係はゼロ
- リスナーが多すぎる場合の自動メモリリーク警告機能を搭載

## 使い方

`EventEmitter`クラスをインポートしてインスタンス化します。このAPIは、Node.jsのAPIのドロップインリプレイスメント（そのまま置き換え可能）として設計されています。

```javascript
import EventEmitter from "https://code4fukui.github.io/events/events.js";

const myEmitter = new EventEmitter();

myEmitter.on("event", () => {
  console.log("イベントが発生しました！");
});

myEmitter.once("special", (arg) => {
  console.log(`これは一度だけ実行されます。引数: ${arg}`);
});

myEmitter.emit("event");
//> イベントが発生しました！

myEmitter.emit("special", "data");
//> これは一度だけ実行されます。引数: data

myEmitter.emit("event");
//> イベントが発生しました！

myEmitter.emit("special", "more data");
// 'once' リスナーが削除されているため、何も起こりません。
```

## API

このモジュールは、標準的なNode.jsの`EventEmitter` APIを実装しています。`on`、`emit`、`once`、`removeListener`、`setMaxListeners`などのメソッドの完全なリストについては、[公式のNode.js EventEmitterドキュメント](https://nodejs.org/api/events.html#class-eventemitter)を参照してください。

## ビルド方法

このプロジェクトではDenoを使用しています。配布用にソースのTypeScriptファイルを単一のJavaScriptファイルにバンドルするには、以下のコマンドを実行します。

```sh
deno bundle events.ts events.js
```

## ライセンス

MIT License — 詳細は [LICENSE](LICENSE) を参照してください。
