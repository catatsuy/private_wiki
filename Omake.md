#おまけ

## ssh
### 鍵生成

    ssh-keygen -t rsa

## お手軽サーバー

    python -m SimpleHTTPServer 8080

## Basic認証
.htaccess
 
    AuthType Basic
    AuthName "メッセージ"
    AuthUserFile ファイルの場所
    require valid-user

## htpasswd

    htpasswd -c ファイル名 ユーザ名

## postfix
### alias
`/etc/aliases` にて
    
    名前: 別名

そして

    sudo newaliases

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


## scss
### 圧縮

    sass --style compressed style.scss:style.css

