# 3-1. docker container --Learned
## Jenkins
マスター/スレーブ構成のJenkinsをローカル環境にdocker-composeで構築する

※引用元：[docker-composeでのJenkins構築](https://qiita.com/KWS_0901/items/34d09b472bea9f5227a7)  
※引用元：[Jenkins 最新情報](https://hub.docker.com/_/jenkins?tab=tags&page=1&ordering=last_updated)

### マスターコンテナの作成
1. docker-compose.ymlファイルを用意する  
`~/docker/docker-jenkins$ vi docker-compose.yml`
1. jenkins_homeディレクトリの作成と権限変更  
`~/docker/docker-jenkins$ mkdir jenkins_home`  
`~/docker/docker-jenkins$ sudo chown -R 1000:1000 jenkins_home`
1. マスターコンテナの起動  
`~/docker/docker-jenkins$ docker-compose up -d`
1. コンテナIDを確認し、マスターコンテナに入る  
`$ sudo docker ps`  
`$ sudo docker exec -it <コンテナID> /bin/bash`
1. 管理者パスワードを取得  
`$ cat /var/jenkins_home/secrets/initialAdminPassword`  
45550eb526dc4682a5529a7d2488ccff
1. jenkins_home/.ssh/にSSH認証キーを作成する  
`$ ssh-keygen -t rsa -C ""`
1. マスターコンテナを停止する  
`(jenkinsのdocker内)$ exit`  
`$ sudo docker-compose stop`

### スレーブコンテナの作成
1. スレーブコンテナ用のDockerFileを作成し、docker-compose.ymlと同一のフォルダに格納する  
`~/docker/docker-jenkins$ vi DockerFile_SLAVE`
1. docker-compose.ymlにスレーブコンテナ用のサービス設定を追加する  
`~/docker/docker-jenkins$ vi docker-compose.yml`
1. コンテナを起動  
`~/docker/docker-jenkins$ sudo docker-compose up -d`

## knowledge
1. 自分のナレッジベース用にknowledgeコンテナをDockerFile/docker-composeを用いて起動する  
※参照先：[knowledgeの構築](https://syachiku.net/knowledge-install/)  
※参照先：[docker-knowledgeのDockerFile Github](https://github.com/support-project/docker-knowledge)
1. DockerFileのダウンロード  
`~$ cd ~/docker/`  
`~/docker$ git clone https://github.com/support-project/docker-knowledge.git`
1. docker-compose.ymlを自環境向けにカスタマイズ  
`~/docker/docker-knowledge$ vi docker-compose.yml`  
&nbsp;&nbsp;&nbsp; PORT 8080:8080  
&nbsp;&nbsp;&nbsp; POSTGRES_PASSWORD=*****  
1. cocker-composeから構築する  
`~/docker/docker-knowledge$ sudo docker-compose up -d`  
&nbsp;&nbsp;&nbsp; up : 作成と開始  
&nbsp;&nbsp;&nbsp; -d : デーモン状態で起動  
コンテナの起動状態を確認  
`$ docker-compose ps`

## Jira/Confluence
※参照先：[Confluence](https://qiita.com/iguchikoma/items/97128b3d3bfbbe7e71a4)  
`$ docker volume create --name jiraVolume`  
`$ docker run -v jiraVolume:/var/atlassian/application-data/jira --name="jira" -d -p 8080:8080 atlassian/jira-software`  
`$ docker volume create --name confluenceVolume`  
`$ docker run -v confluenceVolume:/var/atlassian/application-data/confluence --name="confluence" -d -p 8090:8090 -p 8091:8091 atlassian/confluence-server`

## CentOS 8
※参照先：[CentOS 8のイメージダウンロード・起動](https://qiita.com/witchcraze/items/bc05f8fd90bea2dc333f)  
`$ sudo docker pull centos:8`  
`$ sudo docker images`  
`$ sudo docker run -it --rm centos:8 /bin/bash`  
&nbsp;&nbsp;&nbsp; -it : コンテナの標準入力を開く、ttyを使う  
&nbsp;&nbsp;&nbsp; --rm : 実行完了後にコンテナを削除する

## Taiga
### インストール
1. リポジトリのclone  
`$ git clone https://github.com/kaleidos-ventures/taiga-docker.git`  
`$ cd taiga-docker`  
`$ git checkout stable`
1. アプリを起動する  
`$ ./launch-all.sh`  
  
※引用元：[Taiga 30min setup](https://resources.taiga.io/30min-setup/)  
※引用元：[Github](https://github.com/kaleidos-ventures/taiga-docker)
