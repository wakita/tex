# このディレクトリの内容について

Latexmk を使って文書を執筆するときのためのツールです．環境変数を設定して起動すれば，一気に論文執筆環境に没入できます．わたしの環境はOS XのMacTex (texlive 2013版) です．LinuxやWindowsでも少し変更すれば利用できるはずです．OS Xをご利用の場合はプレビューアとしてSkimをご利用ください．

-----
## 使用方法

本Gitリポジトリをインストールします．便宜上，インストールした場所を $HOME/lib/tex ということにします．

article2014 という論文執筆のプロジェクトを開始することとします．この執筆のためのプロジェクトを用意することとしましょう．わたしは以下のようなフォルダ構成に整えます．

- $HOME/Dropbox/research/paper/article2014/
    - img/ (画像を保存するためのフォルダ)
    - lib/ (設定ファイルを保存するためのフォルダ)
        - main (この執筆プロジェクトのための latexmk の設定ファイル．[設定例](https://github.com/wakita/tex/blob/master/mk/conf.pdflatex)．)
    - sty/ (書式設定のファイルを保存するためのフォルダ)
    - tex/ (文書ファイルを保存するためのフォルダ)
        - draft.tex
        - main.tex
        - section1.tex
        - section2.tex

この構成は私のやり方で，別にこれに従う必要はありません．たとえば，サブフォルダを作成せずに article2014 の下にすべてのファイルを保存するやり方でも構いません．

上の構成のなかでひとつだけ必須のファイルがあります．それは latexmk のための設定ファイルです．この内容は以下のようなものです．conf.pdflatexが設定例ですので参考にして下さい．

    $build = "ビルド手段：pdflatex, platex, uplatex のいずれか";
    @default_files = ("論文のメインファイルのパス：例 tex/main");
    require "$ENV{HOME}/lib/tex/mk/build";

これで準備ができました．あとは latexmk -gg -silent -r lib/main を実行するだけです．タイピングが面倒ならば，alias に登録して下さい．

-----
## 設定ファイルの構成

`build`
:   Latexmkを利用するための共通設定．
