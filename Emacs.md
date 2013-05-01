# Emacs
## .emacs

https://github.com/catatsuy/dot.emacs.d

参照

## 快適に日本語を入力する

ibus-elをinstall後，`~/.Xresouces`に

    Emacs*useXIM: false

して `xrdb ~/.Xresources`

## スペルチェック

aspell の設定をすれば `M-x ispell-buffer` で使えるはずだが，それだと日本語はムリ！みたいなエラーが出る
そこでホームディレクトリに `.aspell.conf` というファイルを作り

    lang en_US

## ssh 先のファイルを開く

    /ssh:user@example.com:/path/to/file

