# 3-1-1. Docker Host
## 環境構築、インストール
### docker-ce
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

### docker-compose
1. docker-composeのインストール  
`$ sudo curl -L https://github.com/docker/compose/releases/download/v2.11.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose`
1. 実行権限の付与  
`$ sudo chmod +x /usr/local/bin/docker-compose`
1. バージョンの確認  
`$ docker-compose --version`

※引用元：[Docker Composeのインストール](https://server-network-note.net/2022/07/docker-ubuntu2204-install/)  
※インストール元；[Release](https://github.com/docker/compose/releases)
