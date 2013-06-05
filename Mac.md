# Mac

## IME 切り替えのキーバインド

ことえりを日本語にするのはC-Shift-j，英語はC-Shift-;
変更する場合は

    林檎<キーボード<キーボードショートカット<前の入力ソース

を変更

## Emacs

### インストール

    EMACS_VER=24.2
    curl -O http://ftp.gnu.org/pub/gnu/emacs/emacs-${EMACS_VER}.tar.gz
    svn co http://svn.sourceforge.jp/svnroot/macemacsjp/inline_patch/trunk inline_patch
    tar xvf emacs-${EMACS_VER}.tar.gz
    cd emacs-${EMACS_VER}
    patch -p0 < ../inline_patch/emacs-inline.patch
    ./configure --with-ns --without-x
    make bootstrap
    make install
    open nextstep/Emacs.app

###  スペルチェック

aspellを使う

    brew install --lang=en aspell

.emacsにプログラムを __絶対パスで指定する__

    (setq-default ispell-program-name "/usr/local/bin/aspell")

ホームディレクトリに`.aspell.conf`というファイルを作り

    lang en_US

を書く

### C-spaceがスポットライトのキーバインドと被っている 

    林檎<システム環境設定<spotlight で変える

## Eclipse

ことえりのキーバインドがEclipseのキーバインドと衝突している

## 小技

Macの`open`コマンド便利

    open .

でカレントディレクトリが開く
