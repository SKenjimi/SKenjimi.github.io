# 3-3. Linux --Learned
## 基本設定
* ホスト名の修正  
file: /etc/hostname
* hostsファイルのホスト名修正  
file: /etc/hosts
* IPアドレス、デフォルトゲートウェイの設定  
/etc/netplan/***.yaml
* DNSの設定  
/etc/systemd/resolved.conf
自ホストのホスト名修正
* sudoers設定  
/etc/sudoers

## 個別設定
### Ubuntu 22.04 LTS
#### System locate
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
`$ pvdisplay `
1. ボリュームグループを表示し確認する  
`$ vgdisplay `
1. 論理ボリュームを表示し確認する  
`$ lvdisplay `

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

### LVMで構成された領域を拡張する方法
`$ vgextent?`
