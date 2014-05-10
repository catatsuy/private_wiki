# Git

## ホームページの更新に使う

`.git/hooks/post-update`に

    #!/bin/sh

    (cd /ディレクトリ && git --git-dir=.git pull)

それで指定のディレクトリで `git clone` しておく
