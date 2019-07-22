# 【Mac】Ruby on Rails環境構築

## Homebrewのインストール

### やり方
1. App storeからXcodeをインストール

2. コマンドライン・デベロッパーツールをインストール
ターミナルから$ xcode-select --installコマンドを発行すると
以下のようにインストールを要求される

ターミナル
$ xcode-select --install
xcode-select: note: install requested for command line developer tools
同時にポップアップが出てくるので"インストール"を選択し利用規約に同意

3. Homebrewをインストール
コマンドはHomebrewのサイトからコピー可能
http://brew.sh/index_ja.html
途中でEnterの入力/インストールユーザのOSパスワードの入力を求められる

ターミナル
```$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"``

4. Homebrewインストール完了確認

ターミナル
```$ brew doctor```
'Your system is ready to brew.'この文字が出れば成功
