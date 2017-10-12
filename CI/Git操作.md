
# GIT 学习

对于GIT来说，可以看做管理代码的数据库，但更一般的称作是配置库。明白这一点，我们就可以通过安装，配置，增，删，改，查，执行,回退等几个方面来学习常见的GIT操作，当然也少不了重要的分支概念。本文并不对GIT的内部实现做讨论。

## 安装

    $cd git-1.7.9

    $./configure

    $make all

    $make install

## 配置信息

## 增
* 初始化仓

* 新增文件

    git add 文件名
## 删
* 删除文件

    git rm 文件名

## 改
* 重命名文件

    git mv 源文件名  目的文件名

* 改变内容

    git add -A
* 改变提交历史

    git reset 

## 查
* 查看修改

    git diff 文件名 ：查看与库上文件的差异

    git diff id1, id2：查看两次提交的差异

    git status　文件目录：查看在此目录下，修改情况

    git blame　文件名：查看该文件每一行最后的修改人信息

    git show id: 查看某次提交的内容

* 查看提交信息

    git log : 查看提交历史信息

## 执行
git commit 

git merge

## GIT BRANCH

## GIT STASH
    用stash 还是用 cherry-pick。 取决于任务的紧急程度与代码量。
