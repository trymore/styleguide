# JavaScriptスタイルガイド


## 全体

### インデント
スペース2個でインデントする。
```javascript
// bad
const hoge = () => {
console.log(1);
}

const hoge = () => {
    console.log(1);
}

// good
const hoge = () => {
  console.log(1);
}
```

### 1行の文字数
基本的に100文字以内に収める。
```javascript
// bad
if(aaaaaaaaaa === bbbbbbbbbb && cccccccccc === dddddddddd && eeeeeeeeee === ffffffffff && gggggggggg === hhhhhhhhhh) {
  console.log('ok');
}

// good
if(aaaaaaaaaa === bbbbbbbbbb &&
   cccccccccc === dddddddddd &&
   eeeeeeeeee === ffffffffff &&
   gggggggggg === hhhhhhhhhh) {
  console.log('ok');
}
```


## 名前空間
グローバルの名前空間の使用は最低限に抑える。
```javascript
// bad
hoge = 1;

// good
const hoge = 1;
```


## 定数
- `const` を使用。
- 全て大文字のスネークケースで命名する。

```javascript
const HOGE_HOGE = 1;
```
参照の再割当てを防げる。


## 変数
- 基本は `const` を使用。
- 参照の再割当てが必要な場合は `const` と同じブロックスコープの `let` を使用する。
- キャメルケースで命名する。
- ローカル変数は `_` 接頭詞をつける。
- 正規表現は `r` 接頭詞をつける。

```javascript
const hogeHoge = 1;
const _fugaFuga = 1;  // ローカル変数
const rPiyoPiyo = /^abc$/;  // 正規表現

// 再割当て時
let hoge = 1;
hoge += 1;
```
`const` 使用時は参照の再割当てを防げる。  
また `const` `let` はブロックスコープの為、関数スコープの `var` よりもスコープ範囲を狭くできる。


## 関数
- キャメルケースで命名する。
- 関数式と関数宣言のどちらを使用してもよい。
- 基本はレキシカルな `this` になるアロー関数を使用する。
- ダイナミックな `this` を使いたい場合は通常の関数を使用する。

```javascript
// 関数式
const hogeHoge = () => {};  // レキシカルなthis
const fugaFuga = function() {};  // ダイナミックなthis

// 関数宣言
hogeHoge() => {};  // レキシカルなthis
function fugaFuga() {};  // ダイナミックなthis
```
ただし関数式は巻き上げがないので注意。


### 引数
- 引数はキャメルケースで命名する。
- オプションの場合は初期値を入れる。

```javascript
const hoge = (fugaFuga, piyo = 0) => {};
```


## クラス・コンストラクタ
クラスが使える場合はコンストラクタではなく、クラスを優先して使用する。

### クラス・コンストラクタの命名
- パスカルケースで命名する。

```javascript
class HogeHoge {};  // クラス
const HogeHoge = () => {};  // コンストラクタ
```

### インスタンスメソッド
- キャメルケースで命名する。
- ローカルメソッドは `_` 接頭詞をつける。

```javascript
class A {
  hogeHoge() {}
  _fugaFuga() {}  // ローカルメソッド
}
```

### インスタンスメンバ
- 基本はキャメルケースで命名する。
- 基本は `constructor` 内で宣言する。
- ローカルメンバは `_` 接頭詞をつける。
- 定数の場合は全て大文字のスネークケースで命名する。

```javascript
class A {
  constructor() {
    this.hogeHoge = 1;
    this._fugaFuga = 1;  // ローカルメンバ
    this.HOGE_HOGE = 1;  // 定数
    this._FUGA_FUGA = 1;  // ローカル定数
  }
}
```

### クラスメソッド
- キャメルケースで命名する。
- ローカルメンバは `_` 接頭詞をつける。

```javascript
class A {
  static hogeHoge() {}
  static _fugaFuga() {}  // ローカルメソッド
}
```

### クラスメンバ

#### 変更がない場合
- 基本はキャメルケースで命名する。
- getter を使って宣言する。
- ローカルメンバは `_` 接頭詞をつける。
- 定数の場合は全て大文字のスネークケースで命名する。

```javascript
class A {
  static get hogeHoge() {
    return 1;
  }

  static get _fugaFuga() {  // ローカルメンバ
    return 1;
  }

  static get HOGE_HOGE() {  // 定数
    return 1;
  }

  static get _FUGA_FUGA() {  // ローカル定数
    return 1;
  }
}
```

#### 変更がある場合
- 可能ならクラス内で宣言する。
- キャメルケースで命名する。
- ローカルメンバは `_` 接頭詞をつける。

```javascript
class A {
  static hogeHoge = 1;
  static _fugaFuga = 1;  // ローカルメンバ
}
```
※現状の ECMAScript の仕様では不可だが、クラス内で宣言することで分かりやすくする。

クラス内で宣言出来ない場合はクラス定義後に宣言する。
```javascript
class A {}
A.hogeHoge = 1;
```


## 比較演算子
`===`、`!===` で比較する。
```javascript
if(a === b) {}
```
`==` は曖昧な比較でバグを生む可能性がある。
値がないことを調べる場合のみ `== null` で比較する。


## コメント
- 名称だけでは分かりづらい箇所には、コメントを記述するようにする。
- [ESDoc](https://esdoc.org/) に準拠したコメントを推奨。


## セレクタ
JavaScript から使用するクラスには `js-` プレフィクスをつける。
```html
<div class="js-hoge"></div>
```

CSS に要素の状態を伝達するためのクラスには `is-` プレフィクスをつける。
```css
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
外部ドメインの JavaScript リソースをロードしない。  
コードの変質に気づくことが困難でセキュリティ上、その他のリスクが存在するため。


## コンパイラ・トランスパイラ
基本は以下のどれかを使用する。

### [CoffeeScript](http://coffeescript.org/)
JavaScript がもつ Bad Parts を排除できる。

### [Babel](https://babeljs.io/)
ECMAScript の最新仕様で記述できる。

### [TypeScript](https://www.typescriptlang.org/)
静的型付けを使用して記述できる。
