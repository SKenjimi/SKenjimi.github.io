# 6-2. ESXi --PoC
## 仮想基盤情報
場所 : 某サイト

### vSwitch
モード変更

### vCenterなしでの仮想マシンのクローン作成
1. ESXiホストのSSHを有効化し、CLIでアクセスする
1. 新規仮想マシンのホスト名で新しいフォルダを作成する  
`# cd /vmfs/volumes/datastore1 `  
`# mkdir <new vm name>`
1. 元となる仮想マシンのvmdk, vmxファイルをコピーする  
`# vmkfstools -i <original vm name>/<original vm name>.vmdk <new vm name>/<new vm name>.vmdk -d thin`  
`# cp -p <original vm name>/<original vm name>.vmx <new vm name>/<new vm name>.vmx`
1. vimを使って仮想マシンの構成情報を修正する  
vimの置換オプション： :%s/\<original vm name\>/\<new vm name\>/g  
`# vi <new vm name>/<new vm name>.vmx`
1. Web UIの「データストア　ブラウザ」にてコピーを確認する
1. 「仮想マシンの登録」を押下し、コピーした仮想マシンの登録を行う
1. 仮想マシンを起動し、起動時に質問が聞かれるので「コピーした」と回答する
1. ホスト名設定とIP設定が元の仮想マシンのままなので、取り扱いに気をつける


※引用元：[ESXi上の仮想マシンのクローンの作成](https://ameblo.jp/shinnaka54/entry-12642395278.html)

## 仮想マシンの管理ルール
### Ubuntu 22.04 LTS
* パッケージファイルは常にアップデートし、最新版とする  
（ただし、アップグレード時にスナップショットを取得し一定期間保持すること）

## 設定
### 共通設定　（Ubuntu22.04）
[OSの基本設定](../3-Learned/3-3-linux.md)

### 個別設定 (dev-docker Ubuntu22.04)
#### Gitの初期セットアップ
1. Gitの利用ユーザー名の指定  
`$ git config --global user.name <YOUR NAME>`
1. Gitの利用メールアドレスの指定  
`$ git config --global user.email <YOUR EMAIL>`

#### Docker環境の構築
* [Dockerホストの環境構築](../3-Learned/3-1-docker/3-1-1-docker-host.md)
* dockerのデータファイル格納先： \/docker-image
