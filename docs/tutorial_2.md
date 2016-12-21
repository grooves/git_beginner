## 作業ディレクトリの作成

まず作業ディレクトリを作成します。

```sh
$ mkdir -p workspaces/forkwell/local_git
$ cd workspaces/forkwell/local_git
```

## リポジトリの初期化

```sh
$ git init
Initialized empty Git repository in /Users/forkwell/workspaces/forkwell/local_git/.git/
$ ls -a
. ..  .git
```

`.git/` という隠しディレクトリがリポジトリになります。このディレクトリに履歴が保存されます。

## "Hello, World" を表示するプログラム

好きなプログラミング言語で "Hello, World" を表示するプログラムを作成してください。下記は Python の例です。

```python
print "Hello world"
```

このファイルをバージョン管理してみましょう。まずは `git status` を実行してください。

```sh
$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	hello.py

nothing added to commit but untracked files present (use "git add" to track)
```

バージョン管理していないので `Untracked files` に表示されています。ヘルプに従い `git add` を実行します。

```sh
$ git add hello.py
$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   hello.py
```

無事にインデックスに登録されました。次に `git commit` でコミットしましょう。

```sh
$ git commit -m "Hello Git World"
[master (root-commit) 53aab76] Hello Git World
 1 file changed, 1 insertion(+)
 create mode 100644 hello.py
$ git status
On branch master
nothing to commit, working tree clean
```

最後に履歴を表示してみます。

```sh
$ git log
commit 53aab7648d48ba6f3004db1159ece77cc7cbc295
Author: sinsoku <sinsoku.listy@gmail.com>
Date:   Wed Dec 21 17:57:52 2016 +0900

    Hello Git World
```

## プログラムを更新する

先ほど作成したプログラムにカウントダウンする処理を追加します。

```python
for n in range(3, 0, -1):
    print n

print "Hello world"
```

`git status` を実行します。

```sh
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   hello.py

no changes added to commit (use "git add" and/or "git commit -a")
```

先ほどとヘルプが変わり `git checkout` の説明が表示されています。

- `git add <file>` は変更内容をインデックスに登録します
- `git checkout -- <file>` は変更内容を破棄して、元に戻します

今回は `git add` を実行します。

```sh
$ git add hello.py
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   hello.py
```

コミットします。

```sh
$ git commit -m "Add countdown"
```

ログが2件あることを確認しましょう。

```sh
$ git log
commit a7e5b767b0bb6a31d9bec2cbc71c980a3ebdc778
Author: sinsoku <sinsoku.listy@gmail.com>
Date:   Wed Dec 21 18:10:42 2016 +0900

    Add countdown

commit 53aab7648d48ba6f3004db1159ece77cc7cbc295
Author: sinsoku <sinsoku.listy@gmail.com>
Date:   Wed Dec 21 17:57:52 2016 +0900

    Hello Git World
```

ログを見ると分かるように、新しいコミットが上に表示されます。

## ブランチを作成して、変更してみる

`git branch` コマンドでブランチを作成することができます。

```sh
$ git branch new_feature
$ git branch
* master
  new_feature
```

`git checkout` コマンドでブランチを切り替えることができます。

```sh
$ git checkout new_feature
$ git branch
  master
* new_feature
```

では、ファイルに簡単な変更を加えてみましょう。(感嘆符を追加しました)

```python
for n in range(3, 0, -1):
    print n

print "Hello world!!"
```

この変更をコミットしましょう。

```sh
$ git add hello.py
$ git commit -m "Change message"
```

今回はログを表示するときに `--graph --decorate` のオプションを追加します。

```sh
$ git log --graph --decorate
* commit f0de65ea07fd227a97dbb910c650e76741ce5860 (HEAD -> new_feature)
| Author: sinsoku <sinsoku.listy@gmail.com>
| Date:   Wed Dec 21 19:03:41 2016 +0900
|
|     Change message
|
* commit a7e5b767b0bb6a31d9bec2cbc71c980a3ebdc778 (master)
| Author: sinsoku <sinsoku.listy@gmail.com>
| Date:   Wed Dec 21 18:10:42 2016 +0900
|
|     Add countdown
|
* commit 53aab7648d48ba6f3004db1159ece77cc7cbc295
  Author: sinsoku <sinsoku.listy@gmail.com>
  Date:   Wed Dec 21 17:57:52 2016 +0900

      Hello Git World
```

ブランチの位置が2つあるのが分かります。

## 元のブランチに切り替える

元の `master` ブランチに切り替えてみましょう。

```sh
$ git checkout master
Switched to branch 'master'
```

`hello.py` のファイルが元に戻ります。

## ブランチをマージする

`new_feature` ブランチで変更した内容を `master` ブランチに統合(マージ)してみます。

```sh
$ git merge new_feature
Updating a7e5b76..f0de65e
Fast-forward
 hello.py | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

`hello.py` に `new_feature` 変更が反映されました。
