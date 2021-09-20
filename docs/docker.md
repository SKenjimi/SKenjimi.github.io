---
sort: 1
text: |
  ABCDEFGHIJKLMNOPQRSTUVWXYZ
  abcdefghijklmnopqrstuvwxyz
  1234567890
  一二三四五六七八九十百千萬上中下左右大小春夏秋冬東南西北金木水火土
---


{:.font-body}

# container
## Jenkins

Act/Stb構成の



マスター/スレーブ構成のJenkinsをローカル環境にdocker-composeで構築する

[docker-composeでのJenkins構築](https://qiita.com/KWS_0901/items/34d09b472bea9f5227a7)

[Jenkins 最新情報](https://hub.docker.com/_/jenkins?tab=tags&page=1&ordering=last_updated)

### マスターコンテナの作成
docker-compose.ymlファイルを用意する

`~/docker/docker-jenkins$ vi docker-compose.yml`

jenkins_homeディレクトリの作成と権限変更

`~/docker/docker-jenkins$ mkdir jenkins_home`

`~/docker/docker-jenkins$ sudo chown -R 1000:1000 jenkins_home`

マスターコンテナの起動

`~/docker/docker-jenkins$ docker-compose up -d`

コンテナIDを確認し、マスターコンテナに入る

`$ sudo docker ps`

`$ sudo docker exec -it <コンテナID> /bin/bash`

管理者パスワードを取得

`$ cat /var/jenkins_home/secrets/initialAdminPassword`

\*\*\*\*\*\*\*\*\*\*
<!-- 45550eb526dc4682a5529a7d2488ccff -->

jenkins_home/.ssh/にSSH認証キーを作成する

`$ ssh-keygen -t rsa -C ""`

マスターコンテナを停止する

`(jenkinsのdocker内)$ exit`

`$ sudo docker-compose stop`

### スレーブコンテナの作成

スレーブコンテナ用のDockerFileを作成し、docker-compose.ymlと同一のフォルダに格納する

`~/docker/docker-jenkins$ vi DockerFile_SLAVE`

docker-compose.ymlにスレーブコンテナ用のサービス設定を追加する

`~/docker/docker-jenkins$ vi docker-compose.yml`

コンテナを起動

`~/docker/docker-jenkins$ sudo docker-compose up -d`

## knowledge
自分のナレッジベース用にknowledgeコンテナをDockerFile/docker-composeを用いて起動する

[knowledgeの構築](https://syachiku.net/knowledge-install/)

[docker-knowledgeのDockerFile Github](https://github.com/support-project/docker-knowledge)

DockerFileのダウンロード

`~$ cd ~/docker/`

`~/docker$ git clone https://github.com/support-project/docker-knowledge.git`

docker-compose.ymlを自環境向けにカスタマイズ

`~/docker/docker-knowledge$ vi docker-compose.yml`

&nbsp;&nbsp;&nbsp; PORT 8080:8080

&nbsp;&nbsp;&nbsp; POSTGRES_PASSWORD=\*\*\*\*\*

cocker-composeから構築する

`~/docker/docker-knowledge$ sudo docker-compose up -d`

&nbsp;&nbsp;&nbsp; up : 作成と開始

&nbsp;&nbsp;&nbsp; -d : デーモン状態で起動

コンテナの起動状態を確認

`$ docker-compose ps`

## Jira/Confluence
[Confluence](https://qiita.com/iguchikoma/items/97128b3d3bfbbe7e71a4)

`$ docker volume create --name jiraVolume`

`$ docker run -v jiraVolume:/var/atlassian/application-data/jira --name="jira" -d -p 8080:8080 atlassian/jira-software`

`$ docker volume create --name confluenceVolume`

`$ docker run -v confluenceVolume:/var/atlassian/application-data/confluence --name="confluence" -d -p 8090:8090 -p 8091:8091 atlassian/confluence-server`

## CentOS 8
[CentOS 8のイメージダウンロード・起動](https://qiita.com/witchcraze/items/bc05f8fd90bea2dc333f)

`$ sudo docker pull centos:8`

`$ sudo docker images`

`$ sudo docker run -it --rm centos:8 /bin/bash`

&nbsp;&nbsp;&nbsp; -it : コンテナの標準入力を開く、ttyを使う

&nbsp;&nbsp;&nbsp; --rm : 実行完了後にコンテナを削除する

