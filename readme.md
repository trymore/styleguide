# スタイルガイド


## コーディングガイドライン

### 命名

- 一般的でない省略をしない。数文字の入力のコストよりも、他人が省略された文字列から元の単語を推測するコストが圧倒的に大きいため。
- カラフルな単語を選択する。

### TODO コメント

TODO でタスクの明確化を図る。

```html
<!-- TODO(JSer): スライダの実装 -->
```
```css
/* TODO(JSer): 動的に高さを設定 */
```
```javascript
// TODO(JSer): ロード後に呼び出す
```


## ファイル構成

### エンコード

UTF-8(BOM無し)

### 改行コード

LF

### git

- [.gitignore](https://github.com/trymore/gitignore) をリポジトリのルートに置く

### 資料や納品ファイルの命名

ファイル名でのソートでバージョン順に並ぶ `ファイル名_yymmdd[a-z].拡張子` で命名する。
`[a-z]` は同ファイル同日のバージョン違いで、日付をまたぐとリセットする。

```
styleguide_130912a.zip
styleguide_130912b.zip
styleguide_130912c.zip
styleguide_130913a.zip
...
```

## エディタ

- 空白文字(タブ, 半角スペース, 全角スペース)を表示できるエディタを使う。不要な空白文字でエラーを出さないため。


## 参考とした資料

- [GitHub Styleguide](https://github.com/styleguide)
- [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)
- [一貫性のある慣用的なJavaScriptの書き方](https://github.com/rwaldron/idiomatic.js/tree/master/translations/ja_JP) (原文 [rwaldron/idiomatic.js](https://github.com/rwaldron/idiomatic.js/))
