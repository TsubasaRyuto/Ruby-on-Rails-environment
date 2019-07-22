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
参考動画：　https://dotinstall.com/lessons/basic_localdev_win_v2/38609
CyberDuckを起動する
起動したら、編集メニューの環境設定を選択

ブラウザの設定
```
'.'で始まるファイルを表示をチェック
ダブルクリックしたファイルを外部エディタで開くをチェック
```

外部エディタの設定
```
外部エディタをAtomに設定
```
設定が終わったら再起動

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




