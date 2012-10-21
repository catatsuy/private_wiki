#Mac

##Macの設定で注意/変更すべきこと

###CapsLock/Ctrl/Command周りの設定変更 
    林檎<キーボード<マウス<修飾キー

ただしこの設定は某工大の計算機室だとiMacと自分のアカウントに紐づいた設定になるらしく，以前に使ったiMacでない限り設定は引き継がれない

##Macのキーバインド 
ことえりを日本語にするのはC-Shift-j，英語はC-Shift-;
変更する場合は

    林檎<キーボード<キーボードショートカット<前の入力ソース

を変更

###Emacs
####インストール

    EMACS_VER=24.2
    curl -O http://ftp.gnu.org/pub/gnu/emacs/emacs-${EMACS_VER}.tar.gz
    svn co http://svn.sourceforge.jp/svnroot/macemacsjp/inline_patch/trunk
    inline_patch
    tar xvfz emacs-${EMACS_VER}.tar.gz
    cd emacs-${EMACS_VER}
    patch -p0 < ../inline_patch/emacs-inline.patch
    ./configure --with-ns --without-x
    make bootstrap
    make install
    open nextstep/Emacs.app

####C-spaceがスポットライトのキーバインドと被っている 
    林檎<システム環境設定<spotlight で変える


###Eclipse
ことえりのキーバインドがEclipseのキーバインドと衝突している

###Java
Javaのデフォルトの文字コードがまさかのSHift JIS .bashrcに

    alias javac="javac -J-Dfile.encoding=UTF-8"
    alias java="java -Dfile.encoding=UTF-8"

###TeX

TeXLiveベースの[MacTeX](http://www.tug.org/mactex/)がある

