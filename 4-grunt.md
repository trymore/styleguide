# Grunt

開発タスク管理ツールです。


## セットアップ

GruntはNode環境で動くツールなのでNode環境を構築します。

1. nvmのインストール
Nodeのバージョンマネージャをインストールします。
```bash
git clone git://github.com/creationix/nvm.git ~/.nvm
touch ~/.nvm/nvm.sh > ~/.bash_profile
```

2. Nodeのインストール
Nodeの安定版の最新バージョンをインストールします。
```bash
nvm ls-remote
```
```bash
...
v0.10.26
v0.10.27
v0.10.28
v0.11.0
v0.11.1
...
```
等とアウトプットされるのでマイナーバージョンが偶数の最新バージョン（この例の場合v0.10.28)をインストールします。
```bash
nvm install v0.10.28
```
このバージョンを使うことを設定ファイルに書いておきます。
```bash
touch "nvm use v0.10.28" > ~/.bash_profile
```

3. Gruntのインストール
Nodeインストール時についてくるパッケージマネージャnpmでGruntをインストールします。
```bash
nvm install -g grunt-cli
```
