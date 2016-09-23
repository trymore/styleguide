# JavaScriptスタイルガイド


## インデント
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

## 1行の文字数
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


## 命名規則
オブジェクト、関数、引数、インスタンス、プロパティ名はキャメルケースを使用する。
```javascript
const hogeHoge = 1;

fugaFuga(piyoPiyo) => {};

class A {
  static hogeHoge = 1;
  fugaFuga() {
    this.piyoPiyo = 1;
  }
}
```

クラスやコンストラクタはパスカルケースを使用する。
```javascript
class HogeHoge {}

const FugaFuga = () => {};
```

定数は大文字のスネークケースを使用する。
```javascript
const HOGE_HOGE = 1;

class A {
  static get HOGE_HOGE() {
    return 1;
  }
}
```

プライベートなオブジェクト、関数、インスタンス、プロパティ名は `_`（アンダースコア）接頭詞を使用する。
```javascript
const _hoge = 1;

_fuga() => {};

class A {
  static get _hoge() {
    return 1;
  }
  _fuga() {
    this._piyo = 1;
  }
}
```

正規表現は `r` 接頭詞をつける。
```javascript
const rHoge = 1;
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
`const` を使用。参照の再割当てを防ぐ為。
```javascript
const HOGE_HOGE = 1;
```


## 変数
- 基本は `const` を使用。参照の再割当てを防ぐ為。
- 参照の再割当てが必要な場合は `const` と同じブロックスコープの `let` を使用する。

```javascript
const hoge = 1;

// 再割当て時
let hoge = 1;
hoge += 1;
```
`const`、`let` はブロックスコープの為、関数スコープの `var` よりもスコープ範囲を狭くできる。


## オブジェクト
リテラル構文を使用する。

```javascript
// bad
const hoge = new Object();

// good
const hoge = {};
```


## 配列
リテラル構文を使用する。

```javascript
// bad
const hoge = new Array();

// good
const hoge = [];
```


## 文字列
- シングルクォートを使用する。
- 文字列を生成する場合は、テンプレートリテラルを使用する。
- `eval()` を使用しない。虚弱性を作る危険性がある為。

```javascript
// bad
const hoge = "hello";
const fuga = hoge + ' world'

// good
const hoge = 'hello';
const hoge = `${ hoge } world`;
```


## 関数
- 関数式と関数宣言のどちらを使用してもよい。関数式は巻き上げがないので注意。
- 基本はレキシカルな `this` になるアロー関数を使用する。
- ダイナミックな `this` を使いたい場合は通常の関数を使用する。

```javascript
// 関数式
const hoge = () => {};  // レキシカルなthis
const fuga = function() {};  // ダイナミックなthis

// 関数宣言
hogeHoge() => {};  // レキシカルなthis
function fugaFuga() {};  // ダイナミックなthis
```


### 引数
- オプションの場合は初期値を入れる。
- オプションは末尾に追加する。

```javascript
const hoge = (fuga, piyo = 0) => {};
```


## クラス・コンストラクタ
クラスが使える場合はコンストラクタではなく、クラスを優先して使用する。

### クラス・コンストラクタの命名
```javascript
class Hoge {};  // クラス
const Fuga = () => {};  // コンストラクタ
```

### インスタンスメソッド
```javascript
class A {
  hoge() {}
}
```

### インスタンスメンバ
基本は `constructor` 内で宣言する。
```javascript
class A {
  constructor() {
    this.hoge = 1;
  }
}
```

### クラスメソッド
```javascript
class A {
  static hoge() {}
}
```

### クラスメンバ

#### 変更がない場合
getter を使って宣言する。

```javascript
class A {
  static get hoge() {
    return 1;
  }
}
```

#### 変更がある場合
可能ならクラス内で宣言する。  
現状の ECMAScript の仕様では不可だが、クラス内で宣言することで分かりやすくする。
```javascript
class A {
  static hoge = 1;
}
```

クラス内で宣言出来ない場合はクラス定義後に宣言する。
```javascript
class A {}
A.hoge = 1;
```


## モジュール
モジュールの読み込み、出力は `import`、`export` を使用する。  
標準仕様の為、将来性を考えて。
```javascript
// bad
const Hoge = require('./hoge');
module.exports = Hoge;

// good
import Fuga from './fuga';
export default Fuga;
```


## 比較演算子
- `===`、`!===` で比較する。`==` は曖昧な比較でバグを生む可能性がある為。
- 値がないことを調べる場合のみ `== null` で比較する。

```javascript
if(a === b) {}
```


## コメント
名称だけでは分かりづらい箇所には、コメントを記述するようにする。  
[ESDoc](https://esdoc.org/) に準拠したコメントを推奨。


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
