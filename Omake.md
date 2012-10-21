#おまけ

##.ssh/config

    Host catatsuy.org
      HostName catatsuy.org
      IdentityFile ~/.ssh/id_rsa.catatsuy.org
      User xxxxxx
      Port xxxxxx 
    Host github.com
      HostName github.com
      User git
      IdentityFile ~/.ssh/id_rsa.github
      TCPKeepAlive yes
      IdentitiesOnly yes

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

##MySQL

###特定データベースにアクセスする権限を与える

    grant all privileges on wordpress.* to 'wp_user'@'localhost' identified by 'wp_pass' with grant option;


##scss
###圧縮

    sass --style compressed style.scss:style.css

