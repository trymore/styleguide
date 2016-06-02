# CSSスタイルガイド

- スペース2個でインデントする


## 命名

- id名やクラス名は**hyphens**で命名: `table_of_contents`や`tableOfContents`ではなく`table-of-contents`
- `js-` プレフィクスのついたクラスは CSS から参照しない: `js-` は JS から参照するためにつけるクラス名
- `is-` プレフィクスのついたクラスは状態を表す: CSS と JS の双方から参照する


## マークアップの変更に強いスタイリング

- ノードにスタイルを指定しない: ノード名を変更したらスタイルが無効になってしまうのを防ぐため。
- スタイリングのためにidを使用しない: コーディングレベルでは一度しか出てこないことを保証することは難しく、要件変更のたびに`id`と`class`を変更するのは非合理的。


# Stylusとnibを使用する

CSSをメンテナブルにするため、[Stylus](http://stylus-lang.com/)と[nib](https://tj.github.io/nib/)使って開発する。


# [Stylus](http://stylus-lang.com/)で書く

CSS が持つ Bad Parts を排除する。`mixins`, `@extend` 等を使い作業効率を上げる。
