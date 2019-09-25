# 【Mac】How to set up Ruby on Rails development environment

## Install Homebrew
### Installing the Xcode
You should install the Xcode from App store

### Installing Command Line Tools
```:Terminal
$ xcode-select --install
> xcode-select: note: install requested for command line developer tools
```
A software update popup window will appear, and please choose to confirm this by clicking “Install”, then agree to the Terms of Service when requested.

### Installing Homebrew
Homebrew is the most popular package manager for Mac OS X.
Please paste following script in a Terminal, and press Enter:
``` :Terminal
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

#### Checking whether `Homebrew` is installed
Run the following command to check whether `homebrew` is installed.
``` :Terminal
$ brew doctor
```
It is success if it outputs 'Your system is ready to brew.'


## Install Ruby
### Installing rbenv
rbenv is a tool that you install multiple versions of Ruby and switch Ruby versions.

Run the following command to install `rbenv`
``` :Terminal
$ brew install rbenv
```
Next, run the following command to check whether `rvenv` is installed.
```
$ rbenv --version
2.2.3 (set by ******)  //  you will see latest version here at that time.
```

### Installing ruby-build
Run the following command to install `ruby-build`
```
$ brew install ruby-build
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
```:ターミナル
$ ls ~/

workspaceディレクトリがない場合
$ mkdir ~/workspace

workspaceディレクトリがある場合（上記でworkspaceディレクトリを作成した場合も)
$ cd ~/workspace

$ mkdir rails_practice
$ cd rails_practice
$ mkdir first_app
$ cd first_app
```
* mkdirコマンドは `make directory` の略で、文字の通りディレクトリの作成
* lsコマンドは `list` の略で、指定したディレクトリ内のファイルやディレクトリの一覧を表示する
* cdコマンドは `change directory`の略で、指定したディレクトリへ移動

### bundle init
```:ターミナル
$ bundle init
> Writing new Gemfile to /Users/*****/workspace/rails_practice/first_app/Gemfile
```

### できあがったGemfileのRailsのコメントアウトを外す
Atom(テキストエディタ)でwokspace/rails_practice/first_app/フォルダーを開き、Gemfileを開く
```:Gemfile
source "https://rubygems.org"

gem 'rails', '~> 5.2.3'
```

### Railsのインストール
``` :ターミナル
$ bundle install --path vendor/bundle
Fetching gem metadata from https://rubygems.org/...........
```

###  Railsアプリの作成
```
$ bundle exec rails new .
聞かれたやつは全部 `y` 
```

### ライブラリーのインストール
```
$ bundle install --path vendor/bundle
Fetching gem metadata from https://rubygems.org/...........
```

### Railsアプリケーションの起動
```
$ bin/rails s
```
ブラウザで http://localhost:3000 にアクセスして、
https://railsguides.jp/railsguides/images/getting_started/rails_welcome.png
このような画面になれば成功です。
