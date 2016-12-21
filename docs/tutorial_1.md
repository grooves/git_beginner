## Git のインストール

https://git-scm.com/ から Git をインストールします。インストール後、下記のコマンドで Git のバージョンが表示できることを確認します。

```sh
$ git --version
```

## GitHub のアカウント作成

https://github.com/ でアカウントを作成して下さい。

## 初期設定

Git の初期設定を行います。これらの設定は `~/.gitconfig` に保存されます。

### ユーザー情報

現在の Git の設定を確認します。

```sh
git config -l
```

設定を行います。

```sh
$ git config --global user.name "<user_name>"
$ git config --global user.email "<email>"
```

### 日本語のファイル対応

Git は標準だと日本語を適切に表示できないため、下記の設定を行います。

```sh
$ git config --global core.quotepath false
```

### エディタ

各自、好きなエディタを設定してください。下記は `vi` を設定する例です。

```sh
$ git config --global core.editor vi
```

## Linux/Mac のターミナル基本操作

### man

ヘルプを表示します。

```sh
$ man git
GIT(1)                                                            Git Manual                                                           GIT(1)

NAME
       git - the stupid content tracker

SYNOPSIS
       git [--version] [--help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p|--paginate|--no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]
```

`SYNOPSIS` にコマンドの使い方が書かれており、`[]` のオプションは省略できるものです。

### pwd

現在のディレクトリを表示します。

```sh
$ pwd
/Users/forkwell
```

### ls

ファイルの一覧を表示します。

```sh
$ ls
LICENSE         README.md         docs
```

### cd

ディレクトリを変更します。

```sh
$ pwd
/Users/forkwell
$ cd git_beginner
$ pwd
/Users/forkwell/git_beginner
```

### mkdir

ディレクトリを作成します。

```sh
$ ls
LICENSE         README.md         docs
$ mkdir feedbacks
$ ls
LICENSE         README.md       docs            feedbacks
```

## vi の基本操作

vi では文章を入力するときは `挿入モード` を使い、コマンドを入力するときは `コマンドモード` を使う必要があります。

| コマンド | 効果 |
|----|----|
| ESC | `コマンドモード` に変更します |
| i | `挿入モード` に変更します |
| :q | vi を終了します |
| :w | ファイルを保存します |
| :wq | ファイルを保存して、vi を終了します |
