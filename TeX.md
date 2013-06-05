# TeX

## インストール

TeXLive

## フォントを埋め込む

`/usr/local/texlive/2011/texmf-dist/fonts/opentype/public` 以下にフォントを入れる

Mac なら

    sudo ln -fs "/Library/Fonts/ヒラギノ明朝 Pro W3.otf" ./HiraMinPro-W3.otf
    sudo ln -fs "/Library/Fonts/ヒラギノ明朝 Pro W6.otf" ./HiraMinPro-W6.otf
    sudo ln -fs "/Library/Fonts/ヒラギノ丸ゴ Pro W4.otf" ./HiraMaruPro-W4.otf
    sudo ln -fs "/Library/Fonts/ヒラギノ角ゴ Pro W3.otf" ./HiraKakuPro-W3.otf
    sudo ln -fs "/Library/Fonts/ヒラギノ角ゴ Pro W6.otf" ./HiraKakuPro-W6.otf
    sudo ln -fs "/Library/Fonts/ヒラギノ角ゴ Std W8.otf" ./HiraKakuStd-W8.otf

とやるとシンボリックリンクが貼られる

ヒラギノの場合

    updmap --setoption kanjiEmbed hiragino

詳しい使い方： http://tutimura.ath.cx/ptetex/?%A5%D5%A5%A9%A5%F3%A5%C8%A4%CE%BD%B8%C3%E6%B4%C9%CD%FD

## ページ設定

TeXはWordなどでいうページ設定が難しいとよく言われる
何も設定しなくても上と左に1インチの余白で，そして下と右の余白は設定できない

テキストの長さをzwにすれば余計な計算が必要ない
テキストの長さを適当に設定すると文字の間の余白などを無駄に計算する必要が出てきてしまう
だから日本語一文字の幅であるzwの整数倍で設定すればよい
つまり`\setlength{\textwidth}{40zw}`のようにする

### calcパッケージを利用する

calcを読み込めば+-*/が使えるようになるのでA4の場合は

    \setlength{\oddsidemargin}{(210truemm-\textwidth)/2-1truein}

とすればちょうどど真ん中にテキストがくるようになる textheightを何行と指定する

例えば30行なら

    \setlength{\textheight}{29\baselineskip+\topskip}

とすれば30行になったと思う

まとめ

    \setlength{\textheight}{29\baselineskip+\topskip}
    \setlength{\textwidth}{40zw}
    \setlength{\oddsidemargin}{(210truemm-\textwidth)/2-1truein}
    \setlength{\topmargin}{(297truemm-\textheight)/2-1truein-1truecm}

みたいな感じで設定すると楽(微調整必須)

## パッケージをインストール

    /usr/local/texlive/2011/texmf-dist/tex/platex/

ls-Rを使っているならmktexlsrを忘れずに

## おまけ

### epsファイルをpdfに

    ps2pdf -dEPSCrop -dPDFA -sProcessColorModel#DeviceCMYK -dPDFSETTINGS#/prepress

### プログラムをかく

listingsがいいが，日本語を扱うにはjlistingsが必要

    \usepackage[final]{listings}
    \lstset{                 %listingsの設定
    numbers=left,            %行番号を左
    numberstyle=\scriptsize, %
    stepnumber=1,            %1行おきに行番号を
    numbersep=1zw,           %ソースと行番号の間隔
    lineskip=-0.5zw,         %行間隔 要調整
    basicstyle=\ttfamily     %ttfamily
    }

使い方

    \begin{lstlisting}[language=~~]
    ~~
    \end{lstlisting}
    \lstinputlisting[caption=~~~~,language=java]{~~.java}

### リンク

    \usepackage[dvipdfm,bookmarks=false,bookmarksnumbered=false,colorlinks=false]{hyperref}

### 行間

    \renewcommand{\baselinestretch}{.8}

フォント設定

    \usepackage[sc]{mathpazo}
    \usepackage[scaled]{beramono}
    \usepackage[scaled]{helvet}
