# JavaScriptスタイルガイド


## 全体

### インデント
スペース2個でインデントする。
```
const foo = () => {
  console.log(1);
}
```

### 1行の文字数
基本的に100文字以内に収める。
```
if(aaaaaaaaaa === bbbbbbbbbb &&
   cccccccccc === dddddddddd &&
   eeeeeeeeee === ffffffffff &&
   gggggggggg === hhhhhhhhhh) {
  console.log('ok');
}
```


## 名前空間
グローバルの名前空間の使用は最低限に抑える。
```
const hoge = 1;
```


## 定数
`const` を使用。  
全て大文字で命名する。
```
const HOGE = 1;
```
参照の再割当てを防げる。


## 変数
`const` を使用。  
キャメルケースで命名する。
```
const hoge = 1;
```
参照の再割当てを防げる。  
またブロックスコープの為、関数スコープの `var` よりもスコープ範囲を狭くできる。

参照の再割当てが必要な場合は `const` と同じブロックスコープの `let` を使用する。
```
let hoge = 1;
hoge += 1;
```

ローカル変数は `_` 接頭詞をつける。
```
const _local = 1;
```

正規表現は `r` 接頭詞をつける。
```
const rHoge = /^abc$/;
```


## 関数
キャメルケースで命名する。  
接頭詞に動詞を使用する。  
関数式と関数宣言のどちらを使用してもよい。  
基本はレキシカルな `this` になるアロー関数を使用する。  
ダイナミックな `this` を使いたい場合は通常の関数を使用する。  
```
// 関数式
const getFoo = () => {};  // レキシカルなthis
const getFoo = function() {};  // ダイナミックなthis

// 関数宣言
getFoo() => {};  // レキシカルなthis
function getFoo() {};  // ダイナミックなthis
```
ただし関数式は巻き上げがないので注意。

引数はキャメルケースで命名する。  
オプションの場合は初期値を入れる。
```
const getFoo = (argArg, argOpt = 0) => {};
```


## クラス・コンストラクタ
クラスが使える場合はコンストラクタではなく、クラスを優先して使用する。

### クラス・コンストラクタの命名
パスカルケースで命名する。
```
class PascalCase {};
const PascalCase = () => {};
```

### クラスメソッド
キャメルケースで命名する。  
接頭詞に動詞を使用する。
```
class A {
  getFoo() {}
}
```

ローカルメソッドは `_` 接頭詞をつける。
```
class A {
  _getFoo() {}
}
```

### クラスメンバ
キャメルケースで命名する。
基本は `constructor` 内で宣言する。
```
class A {
  constructor() {
    this.hoge = 1;
  }
}
```

ローカルメンバは `_` 接頭詞をつける。
```
class A {
  constructor() {
    this._hoge = 1;
  }
}
```

#### static で変更がない場合
getter を使って宣言する。
```
class A {
  static get hoge() {
    return 1;
  };
}
```

#### static で変更がある場合
可能ならクラス内で宣言する。
基本はキャメルケースで命名する。
```
class A {
  static hoge = 1;
}
```
※現状の ECMAScript の仕様では不可だが、クラス内で宣言することで分かりやすくする。

クラス内で宣言出来ない場合はクラス定義後に宣言する。
```
class A {}
A.hoge = 1;
```

ローカル変数は `_` 接頭詞をつける。
```
class A {
  static _hoge = 1;
}
```


## 比較演算子
`===`、`!===` で比較する。
```
if(a === b) {}
```
`==` は曖昧な比較でバグを生む可能性がある。
値がないことを調べる場合のみ `== null` で比較する。


## セレクタ
JavaScript から使用するクラスには `js-` プレフィクスをつける。
```
<div class="js-hoge"></div>
```

CSS に要素の状態を伝達するためのクラスには `is-` プレフィクスをつける。
```
.is-selected { display: block; }
```


## データ
データはJavaScript内に記述しない。
特にViewに関わるデータはControllerやModelであるべきJavaScriptが持つべきではない。
JavaScriptはロジックのみを提供し、データは外部のHTMLやJSONやXMLに記述する。

### 画像のパスを書かない
画像のパスはHTMLに、表示の状態はCSSに記述する。
JavaScriptからはノードのクラスを付け替えるという実装を選択する。


## ライブラリ使用上の注意点
外部ドメインの JavaScript リソースをロードしない。コードの変質に気づくことが困難でセキュリティ上、その他のリスクが存在するため。

### [jQuery](http://jquery.com/)や[Zepto.js](http://zeptojs.com/)の使用上の注意点
- 最新バージョンを使う
- `$.get` や `$.post` は使わず、`$.ajax` を使う。エラーハンドリングができないため。
- 複数回参照する jQuery オブジェクトはキャッシュする。DOM へのアクセス回数を減らしパフォーマンスを向上するため。


## コンパイラ・トランスパイラ
基本は以下のどれかを使用する。
- [CoffeeScript](http://coffeescript.org/)
- [Babel](https://babeljs.io/)
- [TypeScript](https://www.typescriptlang.org/)

### CoffeeScript
JavaScript がもつ Bad Parts を排除できる。

### Babel
ECMAScript の最新仕様で記述できる。

### TypeScript
静的型付けを使用して記述できる。
