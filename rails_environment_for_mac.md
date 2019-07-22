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
