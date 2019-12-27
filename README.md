```git
git init
// 状态，是否有需要commits文件
git status
// 本地日志
git log
// 前两个表示所有，最后一个具体文件名
git add -A/./<file>
git rm --cached <file>
// 只是把暂存区内容删除
git unstage
git commit -m ’msg‘
// 强制提交
git commit -a -m
// 查看远程仓库地址
git remote -v
git remote add <name> <url>
git pull
// 表示把远程拉下来，本地指向远程，远程与本地合并，本地更新为最新版
git pull -rebase origin master
// -u表示之后默认branch，不建议使用
git push (-u) <branch name>/master
// PS: 远程 origin/dev。创建完一定要push一次，不然远程无该分支
git checkout -b <name> <branch name>
// 回滚，打印每一次操作记录
git reflog
```

## workflow

### 1. Centralized Workflow集中式工作流

Like Subversion, the Centralized Workflow uses a central repository to serve as the single point-of-entry for all changes to the project. Instead of `trunk`, the default development branch is called `master` and all changes are committed into this branch. This workflow doesn’t require any other branches besides `master`.

> 一个中央仓库，第二个人：git pull -rebase origin master

### 2. Feature Branch Workflow功能分支工作流

The core idea behind the Feature Branch Workflow is that all feature development should take place in a dedicated branch instead of the `master` branch. This encapsulation makes it easy for multiple developers to work on a particular feature without disturbing the main codebase. It also means the `master` branch will never contain broken code, which is a huge advantage for continuous integration environments.

> 管理人删除远程branch，git branch -r -d origin/[branch name]，git push origin origin [branch name]
>
> Developer删除本地branch，先切换到master，git branch -D [branch name]

### 3. Gitflow Workflow（大型版本）

The Gitflow Workflow defines a strict branching model designed around the project release. While somewhat more complicated than the Feature Branch Workflow, this provides a robust framework for managing larger projects.

> master-release-develop features
>
> release，在发布之前才有
>
> hotfix，维护分支有紧急bug

### 4.Forking Workflow（大型版本，两个远程仓库）

The Forking Workflow is fundamentally different than the other workflows discussed in this tutorial. Instead of using a single server-side repository to act as the “central” codebase, it gives every developer a server-side repository. This means that each contributor has not one, but two Git repositories: a private local one and a public server-side one.
