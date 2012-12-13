#Emacs
##.emacs

    ;; Emacsのキルをクリップボード
    (global-set-key "\M-w" 'clipboard-kill-ring-save)
    (global-set-key "\C-w" 'clipboard-kill-region)

    ;; C-hをBSに
    (global-set-key "\C-h" 'backward-delete-char)

    ;; 対応する括弧をハイライト
    (show-paren-mode t)

    ;; スクロール時の移動量を1に
    (setq scroll-step 1)

    ;; find-fileで大文字小文字を区別しない(Documentsのようにディレクトリ名の最初が大文字で始まっていても無視する)
    (setq read-file-name-completion-ignore-case t)

    ;; Menuを隠す
    (custom-set-variables
    '(display-time-mode t)
    '(tool-bar-mode nil)
    '(transient-mark-mode t))
    (custom-set-faces)

    ;; スクロールバーを消す
    (toggle-scroll-bar nil)

    ;; Font設定（Ubuntu専用）
    (set-default-font "DejaVu Sans Mono-10")
    (set-face-font 'variable-pitch "DejaVu Sans Mono-10")
    (set-fontset-font (frame-parameter nil 'font)
    'japanese-jisx0208
    '("Takaoゴシック" . "unicode-bmp")
    )

    ;; iswitchbの設定
    (iswitchb-mode 1)
    ;; (iswitchb-default-keybindings)

    (add-hook 'iswitchb-define-mode-map-hook
    'iswitchb-my-keys)

    (defun iswitchb-my-keys ()
    (define-key iswitchb-mode-map "\C-f" 'iswitchb-next-match)
    (define-key iswitchb-mode-map " " 'iswitchb-next-match)
    (define-key iswitchb-mode-map "\C-b" 'iswitchb-prev-match)
    )

    ;; ibusの設定
    (add-to-list 'load-path "~/.emacs.d/site-lisp/ibus-el")
    (require 'ibus)
    (add-hook 'after-init-hook 'ibus-mode-on)
    (ibus-define-common-key ?\C-\s nil)
    ;; IBusの状態によってカーソル色を変化させる
    (setq ibus-cursor-color '("red" "blue" "limegreen"))
    ;; C-j で半角英数モードをトグルする
    (ibus-define-common-key ?\C-j t)

    ;; YaTeXのもろもろの設定
    (add-to-list 'load-path "~/.emacs.d/site-lisp/yatex")
    (setq YaTeX-kanji-code 4)
    (setq auto-mode-alist
    (cons (cons "\\.tex$" 'yatex-mode) auto-mode-alist))
    (autoload 'yatex-mode "yatex" "Yet Another LaTeX mode" t)
    (setq tex-command "platex")
    (setq dvi2-command "xdvi %s.dvi")
    (setq dviprint-command-format "dvipdfmx %s.dvi")
    (setq YaTeX-use-LaTeX2e t)
    (setq YaTeX-use-AMS-LaTeX t)

    (setq YaTeX-inhibit-prefix-letter nil)

    ;; Aspellの設定
    (setq-default ispell-program-name "aspell")
    (eval-after-load "ispell"
    '(add-to-list 'ispell-skip-region-alist '("[^\000-\377]+")))

    ;; インデントをスペースに
    (defun my-c-mode-hook ()
    (c-set-style "linux")
    (setq tab-width 4)
    (setq c-basic-offset tab-width))
    (add-hook 'c-mode-hook 'my-c-mode-hook)
    (setq-default tab-width 4 indent-tabs-mode nil)
    (setq-default indent-tab-mode nil)

    ;; Dropbox内でバックアップファイルを作らない
    (let ((dropbox-directory (expand-file-name "~/Dropbox/"))
    (destination-directory "~/Documents/tmp/"))
    (add-to-list 'auto-save-file-name-transforms
    `(,(concat dropbox-directory "\\([^/]*/\\)*\\([^/]*\\)$")
    ,(concat destination-directory "\\2") t))
    (add-to-list 'backup-directory-alist
    `(,dropbox-directory . ,destination-directory)))
    
    ;; Perlの設定
    (defalias 'perl-mode 'cperl-mode)
    (require 'cperl-mode)

    (setq cperl-indent-level 4
    cperl-close-paren-offset -4
    cperl-continued-statement-offset 4
    cperl-indent-parens-as-block t
    cperl-tab-always-indent t)
    (add-hook 'cperl-mode-hook '(lambda () (setq indent-tabs-mode nil)))
    
    ;; Markdownの設定
    (autoload 'markdown-mode "markdown-mode.el"
    "Major mode for editing Markdown files" t)
    (setq auto-mode-alist
    (cons '("\\.md" . markdown-mode) auto-mode-alist))
    
    ;; linum-mode をいじって Emacs を高速化
    (setq linum-delay t)
    (defadvice linum-schedule (around my-linum-schedule () activate)
    (run-with-idle-timer 0.2 nil #'linum-update-current))

##快適に日本語を入力する
ibus-elをinstall後，`~/.Xresouces`に

    Emacs*useXIM: false

して`xrdb ~/.Xresources`

##スペルチェック
aspellの設定をすれば`M-x ispell-buffer`で使えるはずだが，それだと日本語はムリ！みたいなエラーが出る
そこでホームディレクトリに`.aspell.conf`というファイルを作り

    lang en_US

## ssh 先のファイルを開く

    /ssh:user@example.com:/path/to/file

##PHP

http://sourceforge.net/projects/php-mode/ 

`M-x byte-compile`してから

    (autoload 'php-mode "php-mode" "Major mode for editing php code." t)
    (add-to-list 'auto-mode-alist '("\\.php$" . php-mode))
    (add-to-list 'auto-mode-alist '("\\.inc$" . php-mode))
    

