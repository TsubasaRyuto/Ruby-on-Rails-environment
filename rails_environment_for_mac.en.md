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
Next, you have to check whether `rbenv` is installed.run the following command to check whether `rvenv` is installed.
``` :Terminal
$ rbenv --version
2.2.3 (set by ******)  //  you will see latest version here at that time.
```

### Installing ruby-build
ruby-build is plugin of rbenv provided `rbenv install` so that it install Ruby of different version.

Run the following command to install `ruby-build`
``` :Terminal
$ brew install ruby-build
```

### Output 'eval "$(rbenv init -)"' to the bash_profile
Run the following command
``` :Terminal
$ echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
$ source ~/.bash_profile
```

### Installing Ruby
Run the following command to install 'Ruby' version 2.6.3.
``` :Terminal
rbenv install 2.6.3
```

### Change version of Ruby
Run the following command to change version of 'Ruby'
``` :Terminal
$ rbenv global 2.6.3
$ rbenv rehash
$ ruby -v
> ruby 2.6.3 // (You success if you will see specified number at ruby global)
$ gem -v
> 3.0.1
```

## Install bundler
### Installing bundler
Bundler provides a consistent environment for Ruby projects by tracking and installing the exact gems and versions that are needed.

Run the following command to install bundler with gem
``` :Terminal
$ gem install bundler
```

Also, you have to check installed bundler
``` :Terminal
$ bundle -v
> Bundler version 2.0.2 // you will see latest version here at that time.
```

## Install Rubyh on Rails
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
