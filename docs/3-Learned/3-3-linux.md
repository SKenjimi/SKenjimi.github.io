# 3-3. Linux --Learned
## 共通設定
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

