## リポジトリを Fork する

https://github.com/grooves/git_beginner のリポジトリを Fork します。

![](https://raw.githubusercontent.com/grooves/git_beginner/master/images/fork.png)

少し待つと `<user_name>/git_beginner` のリポジトリが作成されます。

## リポジトリを clone する

自分のリポジトリを `git clone` してみましょう。リポジトリのURLは下記の画像の箇所に表示されます。

![](https://raw.githubusercontent.com/grooves/git_beginner/master/images/clone.png)

`git clone <URL>` を実行します。

```sh
$ cd ~/workspaces/forkwell/
$ git clone https://github.com/sinsoku/git_beginner.git
Cloning into 'git_beginner'...
remote: Counting objects: 11, done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 11 (delta 0), reused 11 (delta 0), pack-reused 0
Unpacking objects: 100% (11/11), done.
$ cd git_beginner
```

## イベントの感想を Pull Request する

今回のイベントに参加した感想を `feedbacks/_template.md` を参考に追加し、 Pull Request をしてみます。

```sh
$ cp feedbacks/_template.md feedbacks/sinsoku.md
$ vi feedbacks/sinsoku.md
# アンケートを記入する
$ git add feedbacks/sinsoku.md
$ git commit -m "Add feedback"
```

## 変更を GitHub のリポジトリに反映する

まだローカルのリポジトリに履歴を保存しただけです。

```sh
$ git log --decorate --graph --all
```

この変更内容を GitHub に反映しましょう。

```sh
$ git push origin master
To github.com:sinsoku/git_beginner.git
   82dd315..788ebf4  master -> master
```

実際に反映されているか GitHub のページを表示して確認してみます。
