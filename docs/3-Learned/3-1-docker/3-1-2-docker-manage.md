# 3-1-2. Docker Manage/Compose

## dockerの操作
#### Dockerホストの操作
###### イメージのダウンロード
`$ docker pull イメージ名[:タグ名]`
###### イメージの一覧表示
`$ docker images -a`
###### イメージの詳細確認
`$ docker inspect コンテナ識別子またはイメージ識別子`
###### イメージの削除
`$ docker rmi イメージ名`
###### 稼働コンテナの操作
`$ docker ps`
###### コンテナの稼働確認
`$ docker stats [コンテナ識別子]`
###### Dockerのバージョン確認
`$ docker version`
###### Dockerの実行環境確認
`$ dcoker info`
#### Docker Hubも含めた操作
###### イメージの検索
`$ docker search　検索キーワード` 　　※Docker Hubに公開されているイメージを検索する
###### Docker Hubへのログイン
`$ docker login [サーバ名]`
###### イメージのアップロード
`$ docker push イメージ名[:タグ名]`
###### Docker Hub からのログアウト
`$ docker logout [サーバ名]`
#### Dockerコンテナの生成/起動/停止
###### コンテナ生成
`$ docker create`
###### コンテナ生成/起動
`$ docker run イメージ名[:タグ名] [引数]`
###### コンテナ生成/起動　(bashを使用して対話的実行)
`$ docker run -it --name "コンテナ名" イメージ名[:タグ名] /bin/bash`
###### コンテナ生成/起動 （バックグラウンド、ポート番号、DNS指定、ホスト名、hosts指定）
`$ docker run -d -p 8080:80 --dns=192.168.X.X --hostname=www.example.com --add-host=www.example.com:192.168.X.X イメージ名[:タグ名] [引数]`　　
###### コンテナ起動
`$ docker start コンテナ識別子`
###### コンテナ停止
`$ docker stop コンテナ識別子`
###### コンテナ再起動
`$ docker restart コンテナ識別子`
###### コンテナ削除
`$ docker rm コンテナ識別子`
#### 稼働中のDockerコンテナの操作
###### 稼働コンテナへの接続
`$ docker attach コンテナ名`
###### 稼働コンテナでプロセス実行
`$ docker exec -it コンテナ名 /bin/bash`
###### 稼働コンテナのプロセス確認
`$ docker top コンテナ名`
###### 稼働コンテナのポート転送確認
`$ docker port コンテナ名`
###### コンテナ内のファイルをコピー
`$ docker cp コンテナ名:/tmp/test.txt /tmp`
###### コンテナ操作のイメージ生成時との差分確認
`$ docker diff コンテナ識別子`
#### Dockerコンテナの保存
###### コンテナからイメージ生成
`$ docker commit コンテナ識別子 [イメージ名:[タグ名]]`
###### コンテナをtarファイル出力
`$ docker export コンテナ識別子`
###### tarファイルからイメージ作成
`$ docker import ファイルまたはURL - [イメージ名:[タグ名]]`
###### イメージの保存
`$ docker save 保存ファイル名 [イメージ名]`
###### イメージの読み込み
`$ docker load -i ファイル`
