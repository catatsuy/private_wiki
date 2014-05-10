# Git

## 設定

### Gitの初期設定

    git config --global user.name "catatsuy"
    git config --global user.emali "catatsuy@catatsuy.org"

### gitignore

https://github.com/github/gitignore

## Github で使う時の `.ssh/config`

    Host github.com
      HostName github.com
      User git
      Port 22
      IdentityFile ~/.ssh/id_rsa.github
      Compression yes

## ホームページの更新に使う

`.git/hooks/post-update`に

    #!/bin/sh

    (cd /ディレクトリ && git --git-dir=.git pull)

それで指定のディレクトリで `git clone` しておく
