# Ubuntu

主にデスクトップ利用

## インストール
[UNetbootin](http://unetbootin.sourceforge.net/)を使うとUSBメモリからいけます

## 設定

### ディレクトリ名を英語に
    LANG=C xdg-user-dirs-gtk-update

### キーバインドをEmacs(Mac)風に

GNOME2
端末にgconf-editorと打つ
/desktop/gnome/interface を選択
gtk_key_theme の値をEmacsに変更

Unity

    sudo apt-get install gnome-tweak-tool

テーマからEmacsに

### Nautilusに端末の中に開くを追加する

    sudo apt-get install nautilus-open-terminal


### 串を刺す

東工大の無線LANは串を刺さないと使えない 通す際の注意点は rootに串を刺すこと

    sudo su

でrootになってそこで

    export http_proxy="http://proxy.noc.titech.ac.jp:3128"
    export ftp_proxy="http://proxy.noc.titech.ac.jp:3128"

とすると使えるようになる あらかじめブラウザから認証を通せば，設定時にパスワード等を記入する必要はない しかしこれだとrootから出た時に設定が消えてしまう

### 設定ファイルなどを完全抹消する

    dpkg -l | grep ***
    dpkg -P ***


### フォント追加

`~/.fonts/xxx.ttf`としてから

    sudo fc-cache -fv ~/.fonts/

これで認識されるようになる 追加されたか確認するときは

    fc-list


### 雑多

#### lha(lzh)ファイルを展開する

    sudo apt-get install lha-sjis

#### rarファイルを展開する

rarファイルは圧縮形式だという認識はしてくれるが，展開はしてくれない

    sudo apt-get install unrar
