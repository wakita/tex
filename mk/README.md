# このディレクトリの内容について

Latexmk を使って文書を執筆するときのための共通設定を保存しています．

-----
## Latexmk の共通設定

`common`
:   Latexmkを利用するための共通設定．

`pdflatex`
:   pdflatexを利用するための設定．commonをちょいと拡張している．

`platex`
:   platexを利用するための設定．commonをちょいと拡張している．

`uplatex`
:   uplatexを利用するための設定．commonをちょいと拡張している．

-----
## スクリプト

以下は上述のLatexmkの設定を活用して，LaTeXプロジェクトをビルドするためのユーティリティスクリプト．これを実行すると，

- （まだ存在してなかったら）作業用ディレクトリを作成する

- 作業用ディレクトリを消去する

- プロジェクトをビルドし，プレビューアを起動する

- 継続的にファイルの更新を監視し，必要に応じてPDFファイルを生成し続ける．

実行パスに置いて，そのまま実行するか，LaTeXプロジェクトにコピーして使って下さい．私はLaTeXプロジェクトに`mk`という名前でコピーしています．

`pdflatex.mk`
:    pdflatexを駆動するスクリプト

`platex.mk`
:    platexを駆動するスクリプト

`uplatex.mk`
:    uplatexを駆動するスクリプト

-----
## インストール

私はこのリポジトリを$DROPBOX/lib/texにインストールして使っています．DROPBOXという環境変数を適宜設定するか，各設定ファイルのパス名を適宜修正して使って下さい．

各*.mkファイルのなかで設定しているmain_tex変数の値は私の慣習に沿ったものです．LaTeXプロジェクトにはtexというサブディレクトリを作成し，そのなかのmain.texをメインファイルとして利用しています．みなさんの流儀にしたがって適宜調整して下さい．

commonのなかで設定されている$aux_dirは作業用のディレクトリです．私はLaTeXプロジェクトはDropboxのどこかに置きつつ，LaTeXの副産物でプロジェクトを汚さないように作業用ディレクトリはDropboxの外の~/projects/tex/...としています．もちろん，/tmp とかでも大丈夫です．ご都合に合わせて適宜，修正して使って下さい．

私のようなMacユーザはPDFビューアとしてSkimを利用するのがよいようです．LinuxやWindowsを利用している方は，それぞれの環境でよいものを指定して下さい．PDFビューアの設定はcommonのなかの$pdf_previewerです．

-----
## 使い方

- あなたの執筆プロジェクトに応じて`{pdflatex|platex|uplatex}.mk`スクリプトをプロジェクトディレクトリにコピーし，スクリプトの`main_tex`の値を適宜，あなたの文書の構成に合わせて設定する．