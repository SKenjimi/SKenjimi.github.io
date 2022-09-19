# 6-2. ESXi --PoC
## 仮想基盤情報
場所 : 某サイト

### vSwitch
モード変更

### 仮想マシン（Ubuntu20.04）
#### 共通設定
* /ete/hostname  
ホスト名の修正
* /etc/hosts  
自ホストのホスト名修正
* /etc/netplan/***.yaml  
IPアドレス、デフォルトゲートウェイの設定
* /etc/systemd/resolved.conf  
DNSの設定

#### 個別設定
* 
