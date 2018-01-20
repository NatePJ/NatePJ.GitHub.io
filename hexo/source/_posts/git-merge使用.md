---
title: git merge使用
date: 2018-01-20 11:29:52
tags:
 - git
categories:
---
# git merge使用

---

在本地`git clone [url]`拉下仓库的代码。(在github上[url]对应着两种不同的方式，SSH或者HTTPS，在此不做过多赘述)

> clone代码的时候，首先需要确定clone哪一个分支的代码，默认clone
> master分支的代码，如果想clone其他分支的代码，可以使用命令 `git clone -b branch_name`
> branch_name（branch_name为读者想clone的分支的名字）
> 如果还未建立分支，文末对使用到的命令进行总结会有建立分支的介绍，不懂怎么建立分支的朋友可以查看另一篇详细介绍。




---
## 使用步骤

 1. `git clone [url]`，clone远程仓库master分支代码。确定本地代码是属于哪一个分支（根据第1步中clone的分支确定），本文以 master 分支为例，建立的新分支为 branch_test 。
 2. `cd project_path`(project_path为clone项目本地路径)，进入到项目中，默认分支在clone时的 master 分支上。现在可以对代码进行修改。
 3. `git add .`和`git commit -m "xxx"`(xxx为此次提交修改的描述)。每次需要merge时，先把当前分支上的代码，如果需要merge的代码在远程分支上面，则需要`git pull`拉下代码。
 4. `git checkout branch_test` ，切换到 branch_test 分支上面（这里为读者自己建立的分支）。
 5.  `git pull`,在 branch_test 分支上保证为最新的代码。
 6. `git merge master` ，现在可以在 branch_test 上使把 master 分支的代码 merge 到  branch_test 分支上面。
 7. `git push origin branch_test` ，在没有冲突的情况下面提交代码到远程仓库上面。
 8. 若有冲突，则需要先在 branch_test 分支上面 `git add .` 和 `git commit -m "xxx"`(xxx为此次提交修改的描述)提交本地冲突代码，再使用第7步骤提交到远程仓库。
 9. 如果在有冲突的情况下，可以`git clone -b branch_test .git`拉下代码查看出现冲突的地方会标出来。

> 如果本地代码已经存在，从第3步开始操作。
现在IDE都有很强大的版本控制功能，可以将上述步骤都交给IDE操作，可以很好的解决冲突。
如果merge没有更新，先确定分支更新代码是否提交，没有提交， `git checkout branch_name` 切换到修改代码分支，从第3步开始执行。
如果push代码没有更新，确定是否出现冲突，merge的代码没有提交。

---
## 命令总结
|命令|作用|
|---
|`git merge [branch]`|当前分支为目标分支，需要将[branch]分支上的代码merge到当前分支上面
|`git checkout [branch-name]`|切换分支到目标分支
|`git clone [url]`|clone远程仓库代码，默认master
|`git clone -b branch_name`|clone指定分支代码，branch_name为指定分支名
|`git pull`|拉去远程分支上面的代码
|`git add .` `git add [file]`|暂存区把修改的文件先保存，add 和 . 中间都空格
|`git commit -m "[descriptive message]"`|在版本历史记录中永久记录文件快照https://segmentfault.com/a/1190000005638174
|`git push [alias] [branch]`|提交代码到远程仓库




