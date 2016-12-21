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

## イベントの感想を追加する

今回のイベントに参加した感想を `feedbacks/_template.md` を参考に追加しましょう。まず最初にブランチを作成し、切り替えます。

```sh
$ git checkout -b feedback
Switched to a new branch 'feedback'
```

次にアンケートを記入してコミットします。

```sh
$ cp feedbacks/_template.md feedbacks/sinsoku.md
$ vi feedbacks/sinsoku.md
# アンケートを記入する
$ git add feedbacks/sinsoku.md
$ git commit -m "Add feedback"
[feedback 666e341] Add feedback
 1 file changed, 9 insertions(+)
 create mode 100644 feedbacks/sinsoku.md
```

## 変更を GitHub のリポジトリに反映する

まだ変更内容はローカルリポジトリに保存されただけで、 GitHub のリポジトリには反映されていません。

```sh
$ git log --decorate --graph --all
* commit 666e3418bff1090b879609f216a9773bd894ead3 (HEAD -> feedback)
| Author: sinsoku <sinsoku.listy@gmail.com>
| Date:   Wed Dec 21 19:27:48 2016 +0900
|
|     Add feedback
|
* commit ae9bcd9ffdca35a7af4388a4864e586dab39bbd2 (origin/master, origin/HEAD, master)
| Author: sinsoku <sinsoku.listy@gmail.com>
| Date:   Wed Dec 21 19:08:48 2016 +0900
|
|     :sparkles: Add text for branch and merge
|
```

この変更内容を GitHub に反映しましょう。

```sh
$ git push origin feedback
Counting objects: 3, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 310 bytes | 0 bytes/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local objects.
To github.com:sinsoku/git_beginner.git
 * [new branch]      feedback -> feedback
```

実際に反映されているか GitHub のページを表示して確認してみます。

## Pull Request を送信する

先ほど push したブランチが画面に出ていますので、 `Compare & pull request` のボタンを押します。

![](https://raw.githubusercontent.com/grooves/git_beginner/master/images/pull_request.png)

Pull Request の作成画面になるので、 `Create pull request` を押して、送信します。

![](https://raw.githubusercontent.com/grooves/git_beginner/master/images/create_pull_request.png)
