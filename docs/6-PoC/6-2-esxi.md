# 6-2. ESXi --PoC
## 仮想基盤情報
場所 : 某サイト

### vSwitch
モード変更

### vCenterなしでの仮想マシンのクローン作成
1. 「データストア ブラウザ」を開く
1. 新規仮想マシンのホスト名で新しいフォルダを作成する
1. 元となる仮想マシンのnvram, vmdk, vmx, vmsdファイルをコピーする

※引用元：[ESXi上の仮想マシンのクローンの作成](https://ameblo.jp/shinnaka54/entry-12642395278.html)

## 仮想マシン
1. Ubuntu
* パッケージファイルは常にアップデートし、最新版とする  
（ただし、アップグレード時にスナップショットを取得し一定期間保持すること）

### 共通設定　（Ubuntu22.04）
* ホスト名の修正  
file: /ete/hostname
* hostsファイルのホスト名修正  
file: /etc/hosts
* IPアドレス、デフォルトゲートウェイの設定  
/etc/netplan/***.yaml
* DNSの設定  
/etc/systemd/resolved.conf
自ホストのホスト名修正
* sudoers設定  
/etc/sudoers

### 個別設定 (Ubuntu22.04)
#### Gitの初期セットアップ
1. Gitの利用ユーザー名の指定  
`$ git config --global user.name <YOUR NAME>`
1. Gitの利用メールアドレスの指定  
`$ git config --global user.email <YOUR EMAIL>`

#### docker-ceのインストール
1. 関連パッケージのインストール  
`$ sudo apt update`  
`$ sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release`
1. Dockerの公式GPGキーを追加  
`$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`
1. リポジトリの追加  
`$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`
1. リポジトリのソースリストのファイルを確認し、 22.04LTSのコードネーム「jammy」かつ安定版であることを確認する  
`$ cat /etc/apt/sources.list.d/docker.list`  
`deb [arch=amd64 signed-by=/usr/share/****.gpg] https://download.docker.com/linux/ubuntu   jammy stable`
1. 一旦パッケージを最新化  
`$ sudo apt-get update`
1. リポジトリ追加により新たに取得できたdocker-ceのパッケージ情報を確認  
`$ sudo apt info docker-ce`
1. 最新版のdocker-ceのインストール  
`$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin`
1. dockerユーザーを自グループに追加  
`$ sudo usermod -aG docker <your-user>`
1. 再ログインし、バージョンを確認  
`$ sudo docker version`

※引用元：[Ubuntu 22.04への最新版dockerのインストール](https://self-development.info/ubuntu-22-04-lts%E3%81%B8%E3%81%AE%E6%9C%80%E6%96%B0%E7%89%88docker%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB/)

#### docker-compose のインストール
1. docker-composeのインストール  
`$ sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`
1. 実行権限の付与  
`$ sudo chmod +x /usr/local/bin/docker-compose`
1. バージョンの確認  
`$ **docker-compose --version`

※引用元：[](https://server-network-note.net/2022/07/docker-ubuntu2204-install/)
