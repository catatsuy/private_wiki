#Git

##設定

###Gitのエディタをviに

    git config --global core.editor vi

###共通のgitignore設定

    git config --global core.excludesfile ~/.gitignore

で`~/.gitignore`に

##ホームページの更新に使う
`hooks/post-update`に

    #!/bin/sh

    (cd /ディレクトリ && git --git-dir=.git pull)

それで指定のディレクトリでgit cloneしておく
