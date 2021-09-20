# Ubuntu
## System locate
ロケールパッケージのインストール

`$ apt -y install language-pack-ja-base language-pack-ja`

ロケール設定の一覧表示

`$ localectl list-locales`

ロケールの設定確認

`$ localectl`

ロケールの設定変更

`$ localectl set-locale LANG=ja_JP.UTF-8 LANGUAGE="ja_JP:ja"`

ロケールの設定確認

`$ localectl`

