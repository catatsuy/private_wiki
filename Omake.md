#おまけ

## Basic認証

.htaccess

    AuthType Basic
    AuthName "メッセージ"
    AuthUserFile ファイルの場所
    require valid-user

## htpasswd

    openssl passwd パスワード
    
8文字以上の場合はMD5にする

    openssl passwd -1 パスワード

user:pass って感じで書く

## postfix
### alias
`/etc/aliases` にて

    名前: 別名

そして

    sudo newaliases

## screen

デタッチされている screen を一括削除

    rm -rf /var/run/screen/S-ユーザ名/*

## MySQL

### 特定データベースにアクセスする権限を与える

    grant all privileges on wordpress.* to 'wp_user'@'localhost' identified by 'wp_pass' with grant option;

## YAML

### Ruby スクリプト

    # -*- coding: utf-8 -*-
    require 'yaml'
    require 'pp'

    str  = ARGF.read()      # 入力をすべて読み込む
    data = YAML.load(str)   # パースする
    pp data                 # データを表示する
