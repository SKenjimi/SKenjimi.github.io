---
sort: 1
---
# 基本情報
場所 : GCP GCE

# サービス
## knowledge
目的: ナレッジベース保管用

ポート: 8080

アクセス方法: Web

## Jenkins
目的: CI/CD PoC環境用

ポート: 18080

アクセス方法: Web

# ホームディレクトリ
~
<br>
&nbsp;&nbsp;&nbsp;└ docker
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ docker-knowledge

# インストールパッケージ
**docker-ce**
<br>
&nbsp;&nbsp;&nbsp;└ apt-transport-https
<br>
&nbsp;&nbsp;&nbsp;└ ca-certificates 
<br>
&nbsp;&nbsp;&nbsp;└ curl
<br>
&nbsp;&nbsp;&nbsp;└ software-properties-common

**docker-compose**

# 各種手順

## dockerインストール

[dockerインストール(Ubuntu)](https://qiita.com/tkyonezu/items/0f6da57eb2d823d2611d)

[dockerインストール(Ubuntu 20.04LTS)](https://qiita.com/nanbuwks/items/0ba1d13b3cd27e5c6426)

アップデート

`$ sudo apt-get update`

前提ソフトウェアのインストール

`$ sudo apt install apt-transport-https ca-certificates curl software-properties-common`

GPG公開鍵のインストール

`$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`

`$ sudo apt-key fingerprint 0EBFCD88`

aptリポジトリの設定

`$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"`

docker-ceのインストール

`$ sudo apt update`

`$ apt-cache policy docker-ce`

`$ sudo apt install docker-ce`

状態確認

`$ sudo systemctl status docker`

一般ユーザーで実行できるようにする

`$ sudo usermod -aG docker <アカウント名>`

## docker-composeのインストール
[docker-composeのインストール](https://docs.docker.com/compose/install/)

docker-composeの最新版をダウンロード

`$ sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`

パーミッションを付与し、パスのシンボリックリンクを追加

`$ sudo chmod +x /usr/local/bin/docker-compose`

`$ sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose`

バージョンを確認

`$ docker-compose --version`
