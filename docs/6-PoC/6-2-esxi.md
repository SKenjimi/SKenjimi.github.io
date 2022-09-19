# 6-2. ESXi --PoC
## 仮想基盤情報
場所 : 某サイト

### vSwitch
モード変更

### vCenterなしでの仮想マシンのクローン作成
1. 「データストア ブラウザ」を開く
1. 新規仮想マシンのホスト名で新しいフォルダを作成する
1. 元となる仮想マシンのnvram, vmdk, vmx, vmsdファイルをコピーする

※[ESXi上の仮想マシンのクローンの作成](https://ameblo.jp/shinnaka54/entry-12642395278.html)

## 仮想マシン
1. Ubuntu
* パッケージファイルは常にアップデートし、最新版とする（ただし、アップグレード時にスナップショットを取得し一定期間保持すること）

### 共通設定　（Ubuntu20.04）
* /ete/hostname  
ホスト名の修正
* /etc/hosts  
自ホストのホスト名修正
* /etc/netplan/***.yaml  
IPアドレス、デフォルトゲートウェイの設定
* /etc/systemd/resolved.conf  
DNSの設定
* /etc/sudoers

### 個別設定
* 
