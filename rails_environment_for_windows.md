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
こちらのサイトからインストラーをダウンロード後、VirtualBoxをインストールする

## LinuxOSの仮想環境構築
PowerShellにて、Vagrant専用フォルダを作成し、その中に仮想マシンようのフォルダを作成し、移動します。
```:ps 
$ cd　
$ mkdir ubuntu64
$ cd ubuntu64
```
* mkdirコマンドは `make directory` の略で、文字の通りディレクトリの作成
* cdコマンドは `change directory`の略で、指定したディレクトリへ移動（directoryの指定がない場合トップディレクトリに移動）

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

### PuTTyで仮想マシンに接続
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

## CyberDuckで仮想マシンに接続
### CyberDuckのインストール
https://cyberduck.io/download/
こちらのサイトよりインストラー（Cyberduck for windows）をダウンロードする
ダウンロードが完了したら、インストラーを開いてCyberDuckをインストールする

### CyberDuckの設定
参考動画をご覧になる際は、「CyberDuckのインストール」のみにしてください。
続けて、ドットインストールを参考にしてしまうと、途中でうまくいかなくなる可能性がございます。

参考動画：　https://dotinstall.com/lessons/basic_localdev_win_v2/38609

1. CyberDuckを起動する
2. 起動したら、編集メニューの環境設定を選択
3. ブラウザの設定
```
'.'で始まるファイルを表示をチェック
ダブルクリックしたファイルを外部エディタで開くをチェック
```
4. 外部エディタの設定
```
外部エディタをAtomに設定
```
5.設定が終わったら再起動

### CyberDuckで仮想マシンに接続
1. 新規接続を選択
2. プロトコルをFTP -> SFTPへ変更する
3. サーバー： 192.168.33.10
4. ユーザ名： vagrant
5. パスワード： vagrant
6. 接続をクリック　-> 許可

無事接続できたら、色々なフォルダーが出てくると思います。
フォルダー一覧が出てきたら成功

### 接続をブックマーク
1. ブックマークメニューを選択
2. 新規ブックマークを選択
3. ニックネーム：　仮想マシーン（ubuntu）
4. ❌ボタンをクリックして終了

こうすることで、次回からは簡単に接続できるようになります。

## Railsを利用する上で必要なパッケージのインストール
```
$ sudo apt-get update
$ sudo apt-get -y install curl 
$ sudo apt-get -y install g++ 
$ sudo apt-get -y install make
$ sudo apt-get -y install zlib1g-dev
$ sudo apt-get -y install libssl-dev
$ sudo apt-get -y install libreadline-dev
$ sudo apt-get -y install libyaml-dev
$ sudo apt-get -y install libxml2-dev
$ sudo apt-get -y install libxslt-dev
$ sudo apt-get -y install sqlite3
$ sudo apt-get -y install libsqlite3-dev
$ sudo apt-get -y install nodejs
```

## 仮想環境にRubyインストール
### Gitのインストール
```:仮想マシーン（PuTTy）
$ sudo apt-get -y install git
```
gitがインストールされたか確認
```
$ git --version
```

### rbenvのインストール
rbenvをgitからclone
```:仮想マシーン（PuTTy）
$ git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
```
bash_profileに記載する(以下のコマンド実行することで記載されます)
```:仮想マシーン（PuTTy）
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
$ echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
$ source ~/.bash_profile
$ rbenv --version
```
rbenvがインストールされているかを確認する
```:仮想マシーン（PuTTy）
$ rbenv -v
```

### ruby-buildのインストール
ruby-buildとは、rubyをインストールするためのrbenvのプラグイン。
ruby-buildをgitからclone。
```:仮想マシーン（PuTTy）
$ git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
```

### Rubyのインストール
```
$ rbenv install 2.6.3
```
> errorが出たら　`RUBY_CONFIGURE_OPTS=--disable-install-doc rbenv install 2.6.3`
### Rubyのバージョン切り替え
```
$ rbenv global 2.6.3
$ rbenv rehash
$ ruby -v
> ruby 2.6.3 // (ruby globalで指定した数字が表示されていれば成功です)
$ gem -v
> 3.0.3 // ここは3.0.3とは限りません。その時の最新バージョンが表示されます
```

### bundlerインストール
```
$ gem install bundler
$ bundle -v
> Bundler version 2.0.2 // ここは2.0.2とは限りません。その時の最新バージョンが表示されます
```

## Railsインストール
### ターミナル上でディレクトリの作成と移動
```
$ mkdir ~/workspace
$ cd ~/workspace
$ mkdir rails_practice
$ cd rails_practice
$ mkdir first_app
$ cd first_app
```
* mkdirコマンドは `make directory` の略で、文字の通りディレクトリの作成
* lsコマンドは `list` の略で、指定したディレクトリ内のファイルやディレクトリの一覧を表示する
* cdコマンドは `change directory` の略で、指定したディレクトリへ移動

### bundle init
```
$ bundle init
> Writing new Gemfile to /Users/*****/workspace/rails_practice/first_app/Gemfile
```

### できあがったGemfileのRailsのコメントアウトを外す
Atom(テキストエディタ)でwokspace/rails_practice/first_app/フォルダーを開き、Gemfileを開く
```
source "https://rubygems.org"

gem "rails"
```

### Railsのインストール
```
$ bundle install --path vendor/bundle
Fetching gem metadata from https://rubygems.org/...........
```

### Railsアプリの作成
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
$ bin/rails s -b 192.168.33.10
```
ブラウザで `http://192.168.33.10:3000` にアクセスして、 https://railsguides.jp/railsguides/images/getting_started/rails_welcome.png このような画面になれば成功です。



