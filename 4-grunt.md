# Grunt

開発タスク管理ツールです。


## セットアップ

GruntはNode環境で動くツールなのでNode環境を構築します。

### 1. [nvm](https://github.com/creationix/nvm)のインストール
Nodeのバージョンマネージャをインストールします。
```bash
git clone git://github.com/creationix/nvm.git ~/.nvm
source ~/.nvm/nvm.sh
echo "source ~/.nvm/nvm.sh" >> ~/.bashrc
```

### 2. [Node](https://github.com/joyent/node)のインストール
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
echo "nvm use v0.10.28" >> ~/.bashrc
```

### 3. [grunt-cli](https://github.com/gruntjs/grunt-cli)のインストール
コマンドラインからGruntを実行するためのgrunt-cliをインストールします。
```bash
npm install -g grunt-cli
```
