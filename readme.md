# スタイルガイド

- [Markupスタイルガイド](blob/master/markup.md)
- [CSSスタイルガイド](blob/master/css.md)
- [JavaScriptスタイルガイド](blob/master/javascript.md)


## コーディングガイドライン

### 命名

- 一般的でない省略をしない。たった数文字の入力のコストよりも、他人が省略された文字列から元の単語を推測するコストが圧倒的に大きいため。
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

ファイル名でのソートでバージョン順に並ぶ `リポジトリ名_yymmdd[a-z].拡張子` で命名する。
`[a-z]` は同ファイル同日のバージョン違いで、日付をまたぐとリセットする。

```
styleguide_130912a.zip
styleguide_130912b.zip
styleguide_130912c.zip
styleguide_130913a.zip
...
```


## 参考とした資料

- [GitHub Styleguide](https://github.com/styleguide)
- [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)
