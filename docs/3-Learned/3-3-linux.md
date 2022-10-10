# 3-3. Linux --Learned
## 基本設定
### Ubuntu 22.04 LTS
#### 共通
* ホスト名の修正  
file: /etc/hostname
* hostsファイルのホスト名修正  
file: /etc/hosts
* IPアドレス、デフォルトゲートウェイの設定  
file: /etc/netplan/***.yaml
* DNSの設定  
file: /etc/systemd/resolved.conf
自ホストのホスト名修正
* sudoers設定  
file: /etc/sudoers

#### (Additional) System locate
1. ロケールパッケージのインストール  
`$ apt -y install language-pack-ja-base language-pack-ja`
1. ロケール設定の一覧表示  
`$ localectl list-locales`
1. ロケールの設定確認  
`$ localectl`
1. ロケールの設定変更  
`$ localectl set-locale LANG=ja_JP.UTF-8 LANGUAGE="ja_JP:ja"`
1. ロケールの設定確認  
`$ localectl`

### Photon OS 4.0 rev2
#### 共通
* ネットワークの設定    
file: /etc/systemd/network/10-static-eth0.network
* ホスト名の変更  
hostnamectl
* タイムゾーンと時刻同期の設定  
timedatectl
* 各種 Linux コマンド(ツール)のインストール  

※引用元；[PhotonOS 初期セットアップ](https://blog.denet.co.jp/lets-create-a-docker-and-docker-compose-env-using-photon-os/)

## その他
### LVMでディスク追加する方法
1. 仮想基盤側で物理ディスクを追加、作成しておく
1. OS上でブロックデバイスの認識を確認し、対象の物理ボリュームを確認する  
`$ lsblk -S`
1. 対象の物理ボリュームの詳細を確認する  
`$ fdisk -l /dev/sdX`
1. 物理ボリュームを初期化する  
`$ pvcreate /dev/sdX`
1. ボリュームグループを作成する  
`$ vgcreate <vg name> /dev/sdX`
1. 論理ボリュームの作成  
`$ lvcreate -l 100%FREE -n <lv name> <vg name>`
1. ファイルシステムの作成し、マウントする  
`$ mkfs.ext4 /dev/<vg name>/<lv name>`  
`$ mount /dev/<vg name>/<lv name> <mount point>`
1. 物理ボリュームを表示し確認する  
`$ pvdisplay /dev/sdX`
1. ボリュームグループを表示し確認する  
`$ vgdisplay <vg name>`
1. 論理ボリュームを表示し確認する  
`$ lvdisplay /dev/<vg name>/<lv name>`

### ディスクを起動時にマウントする方法
1. 対象のディスクデバイスを確認する  
`$ fdisk -l`
1. UUIDをチェックする  
`$ blkid /dev/sdX`
1. \/etc\/fstabにマウント設定を追記する  
`$ vi /etc/fstab`  
追記事項: UUID=xxxxxxxx-xxxxxxxxx       <mount point> ext4    defaults        0       0
1. 再起動し、マウントされているか確認する  
`$ shutdown -h now`  
`$ cat /etc/mtab`

### LVMで構成された領域を拡張する方法（オンライン拡張）
1. 物理ボリュームを拡張する  
`$ vgresize /dev/sdb`
1. 論理ボリュームを拡張する  
`$ lvextend -l +100%FREE <lv name>`
1. ファイルシステムを拡張する  
`$ resize2fs /dev/<vg name>/<lv name>` ※ext4の場合
