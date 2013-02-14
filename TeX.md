# TeX

## インストール

TeXLive


## フォントを埋め込む
`/usr/local/texlive/2011/texmf-dist/fonts/opentype/public` 以下にフォントをいれて

ヒラギノの場合

    updmap --setoption kanjiEmbed hiragino

昔は.mapファイルを編集する必要があったが現在はupdmapを使うと非常に簡単にフォントの設定を変えることができる
（もちろんマイナーなフォントの設定をする際は.mapファイルの編集は必要であるが） 詳しい使い方はhttp://tutimura.ath.cx/ptetex/?%A5%D5%A5%A9%A5%F3%A5%C8%A4%CE%BD%B8%C3%E6%B4%C9%CD%FD 参照


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

## YaTeX

https://github.com/catatsuy/dotfiles/blob/master/.emacs 参照

`/work/template.tex` というファイルが存在すれば，テンプレートとして使用できる


## TeXで簡単に表を使う

TeXで表を扱うならCalc2LaTeXを使うとよい 変換後微調整が必要なことが多いので，今後の変更を考えてどう微調整したのかをコメントに書くなり，量が多い場合スクリプトを作ったほうが良いかもしれない


## パッケージをインストール

    /usr/local/texlive/2011/texmf-dist/tex/platex/

ls-Rを使っているならmktexlsrを忘れずに


## TeXで名刺を作ろう！

dvi wareにページサイズを指定する
dvi ware（日本の場合は十中八九dvipdfmx）にページサイズを指定しなけれ ば，pdfにしたときにサイズがおかしくなる A4などのメジャーなものであれば新ドキュメントクラスならpapersizeオプションで出来るのだが，名刺など特殊なサイズだと指定できないので

    \AtBeginDvi{\special{papersize=91truemm,55truemm}}

のようにしてdvi wareにサイズを伝える


パッケージを読み込む

    \usepackage[dvipdfm]{graphicx,pict2e}%画像・picture環境の拡張 名刺なら必須かと
    \usepackage[T1]{fontenc}
    \usepackage[utf8]{inputenc}%この2つは盲目的に指定してください（文字コードがutf8ならば）
    \usepackage[deluxe,expert]{otf}%dvi wareでフォントをしっかり設定すれば太い明朝・ゴシックの使い分けができます
    \usepackage{okumacro}%ルビが使えるようになります

またフォントをお好みで

    \usepackage[sc]{mathpazo}
    \usepackage[scaled=.8]{beramono}
    \usepackage[scaled=.8]{helvet}

余白等の設定

    \setlength{\hoffset}{0in}
    \setlength{\voffset}{0in}
    \setlength{\headheight}{0in}
    \setlength{\headsep}{0in}
    \setlength{\oddsidemargin}{-1truein}
    \setlength{\topmargin}{-1truein}
    \pagestyle{empty}

\pagestyle{empty}も忘れずに


本文

    \kanjifamily{gt}
    \setlength{\unitlength}{1truemm}
    \begin{picture}(91,55)(0,0)
    \put(x,y){}
    \end{picture}

名刺はゴシック体が多いと思うので最初にゴシックにしています あとはpicture環境でゴリゴリやってください


### まとめ

    \documentclass{jsarticle}
    \AtBeginDvi{\special{papersize=91truemm,55truemm}}
    \usepackage[dvipdfm]{graphicx,pict2e}
    \usepackage[T1]{fontenc}
    \usepackage[utf8]{inputenc}
    \usepackage[sc]{mathpazo}
    \usepackage[scaled=.8]{beramono}
    \usepackage[scaled=.8]{helvet}
    \usepackage[deluxe,expert]{otf}
    \usepackage{okumacro}
    \pagestyle{empty}
    \setlength{\hoffset}{0in}
    \setlength{\voffset}{0in}
    \setlength{\headheight}{0in}
    \setlength{\headsep}{0in}
    \setlength{\oddsidemargin}{-1truein}
    \setlength{\topmargin}{-1truein}
    \begin{document}
    \kanjifamily{gt}
    \setlength{\unitlength}{1truemm}
        \begin{picture}(91,55)(0,0)
         \put(x,y){}
        \end{picture}
    \end{document}


## おまけ

### epsファイルをpdfに

    ps2pdf -dEPSCrop -dPDFA -sProcessColorModel#DeviceCMYK -dPDFSETTINGS#/prepress

### プログラムをかく

listingsがいいが，日本語を扱うにはjlistingsが必要

    \usepackage[final]{listings}
    \lstset{%listingsの設定
    numbers=left,%行番号を左
    numberstyle=\scriptsize,%
    stepnumber=1,%1行おきに行番号を
    numbersep=1zw,%ソースと行番号の間隔
    lineskip=-0.5zw,%行間隔 要調整
    basicstyle=\ttfamily%ttfamily
    }

使い方

    \begin{lstlisting}[language=~~]
    ~~
    \end{lstlisting}
    \lstinputlisting[caption=~~~~,language=java]{~~.java}

### 行間

    \renewcommand{\baselinestretch}{.8}

フォント設定

    \usepackage[sc]{mathpazo}
    \usepackage[scaled]{beramono}
    \usepackage[scaled]{helvet}
