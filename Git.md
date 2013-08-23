# Git

## 設定

### Gitの初期設定

    git config --global user.name "catatsuy"
    git config --global user.emali "catatsuy@catatsuy.org"
    git config --global core.editor vi
    git config --global color.ui auto
    git config --global color.diff auto
    git config --global color.status auto
    git config --global color.branch auto
    git config --global merge.ff false
    git config --global core.autocrlf input

### 共通のgitignore設定

    git config --global core.excludesfile ~/.gitignore

で `~/.gitignore` に

https://github.com/github/gitignore ここ参照

## Github で使う時の `.ssh/config`

    Host github.com
      HostName github.com
      User git
      IdentityFile ~/.ssh/id_rsa.github
      TCPKeepAlive yes
      IdentitiesOnly yes
      Compression yes
      Ciphers arcfour256

## ホームページの更新に使う

`.git/hooks/post-update`に

    #!/bin/sh

    (cd /ディレクトリ && git --git-dir=.git pull)

それで指定のディレクトリで `git clone` しておく
