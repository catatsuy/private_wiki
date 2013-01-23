# Emacs
## .emacs

https://github.com/catatsuy/dotfiles/blob/master/.emacs

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

## PHP

http://sourceforge.net/projects/php-mode/ 

`M-x byte-compile` してから

    (autoload 'php-mode "php-mode" "Major mode for editing php code." t)
    (add-to-list 'auto-mode-alist '("\\.php$" . php-mode))
    (add-to-list 'auto-mode-alist '("\\.inc$" . php-mode))
    

