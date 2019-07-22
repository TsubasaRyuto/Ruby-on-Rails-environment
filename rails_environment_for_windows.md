# 【Windows】Ruby on Rails環境構築

## vagrantのインストール
https://www.vagrantup.com/downloads.html
こちらのサイトからインストールする

インストール後、PowerShellでインストールできているかを確認する
```:PS
$ vagrant -v
```
バージョンが表示されれば成功

## VirtualBoxインストール
https://www.virtualbox.org/wiki/Downloads
こちらのサイトからインストール

## LinuxOSの仮想環境構築
PowerShellにて、Dドライブ直下にVagrant専用フォルダを作成し、その中に仮想マシンようのフォルダを作成し移動します。
```:ps 
$ mkdir C:\Vagrant
$ cd C:\Vagrant
$ mkdir ubuntu64
$ cd ubuntu64
```
* mkdirコマンドは `make directory` の略で、文字の通りディレクトリの作成
* cdコマンドは `change directory`の略で、指定したディレクトリへ移動

### Vagrant初期化
Boxを追加しUbuntuOSで初期化します
https://app.vagrantup.com/boxes/search
こちらのサイトより、インストールするBoxファイルを検索する
今回使用するのは、「ubuntu/trust64」
```:ps
$ vagrant box add ubuntu/trusty64
$ vagrant init ubuntu/trusty64
```

### Vagrantfileを編集
作成されたVagrantfileをテキストエディタで編集し、以下のコメントアウトを外します
```:Vagrantfile
config.vm.network "private_network", ip: "192.168.33.10"
```

### 仮想マシン起動
```:PS
$ vagrant up
```

## PuTTyで仮想マシンに接続
PuTTyは仮想マシンにSSH接続するためのツール

### PuTTyのインストール
https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
こちらのサイトからPuTTyのインストラー（Package file: putty-arm64-0.72-installer.msi）をダウンロードし
PuTTyをインストールする

### PuTTyの起動と仮想マシンへのログイン
PuTTyを起動する
起動したら、接続先の設定をする
```
接続先ホスト名： 192.168.33.10
接続先ポート： 22
コネクションタイプ：　SSH
```
PuTTy Security Alertが出てくると思うので、「はい（yes）」をクリックする

起動する際に、vagrantのユーザー名（login as:）とパスワード（password:）が聞かれるので、入力してenter（return）を押す
```
user_name: vagrant
password: vagrant
```
passwordを入力際の注意点：　入力しても文字が出てくることはないです。注意しましょう。

ここまでで無事PuTTyを起動し、仮想マシンにログインすることができました。
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

gem "rails"
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
$ rails s
```
ブラウザで http://localhost:3000 にアクセスして、
https://railsguides.jp/railsguides/images/getting_started/rails_welcome.png
このような画面になれば成功です。
