# 【Mac】Ruby on Rails環境構築

## Homebrewのインストール

### やり方
#### xcodeのインストール
App storeからXcodeをインストール

#### コマンドライン・デベロッパーツールをインストール

```:ターミナル
$ xcode-select --install
> xcode-select: note: install requested for command line developer tools
```
同時にポップアップが出てくるので"インストール"を選択し利用規約に同意

#### Homebrewをインストール
http://brew.sh/index_ja.html

#### Homebrewインストール完了確認

```:ターミナル
$ brew doctor
```
'Your system is ready to brew.'この文字が出れば成功


## rbenvのインストール
### やり方
```:ターミナル
$ brew install rbenv
$ brew install ruby-build
$ rbenv version
2.2.3 (set by ******) // ここは2.2.3とは限りません。その時の最新バージョンが表示されます
```

bash_profileに記載する(以下のコマンド実行することで記載されます)
```:ターミナル
$ echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
$ source ~/.bash_profile
```

## Rubyのインストール
```:ターミナル
rbenv install 2.6.3
```

## Rubyのバージョン切り替え
```:ターミナル
$ rbenv global 2.6.3
$ rbenv rehash
$ ruby -v
> ruby 2.6.3 // (ruby globalで指定した数字が表示されていれば成功です)
$ gem -v
> 3.0.1 // ここは3.0.1とは限りません。その時の最新バージョンが表示されます
```

## bundlerインストール
```:ターミナル
$ gem install bundler
$ bundle -v
> Bundler version 2.0.2 // ここは2.0.2とは限りません。その時の最新バージョンが表示されます
```

## Railsインストール
ここまで、学習をしてきた方はおそらくworksapceフォルダはあると思いますが、ない場合は適当な場所にworkspaceを作成

### ターミナル上でディレクトリの作成と移動
```
$ mkdir ~/workspace
$ ls ~/workspace
$ cd ~/workspace
$ mkdir rails_practice
$ cd rails_practice
$ mkdir first_app
$ cd first_app
```
* mkdirコマンドは `make directory` の略で、文字の通りディレクトリの作成
* lsコマンドは `list` の略で、指定したディレクトリ内のファイルやディレクトリの一覧を表示する
* cdコマンドは `change directory`の略で、指定したディレクトリへ移動
