
# GIT 学习

对于GIT来说，我们可以把它看做管理代码的数据库，但更一般的称作是配置库。明白这一点，我们就可以通过安装，配置，增，删，改，查，执行，回退等几个方面来学习常见的GIT操作，当然也少不了重要的分支概念。本文并不对GIT的内部实现做讨论。

## 安装

    $cd git-1.7.9

    $./configure

    $make all

    $make install

## 配置信息
每次向版本库提交时，如果都需要输入账户信息，显示非常低效， 更好的方法是版本库记住你的账户信息。此时可以使用git config命令在配置文件中保存你的身份。
如：

    git config user.name "yakamoz"
    git config user.email "yakamoz@gmail.com"

### 配置文件
GIT的配置文件采用.ini文件风格的文本文件。记录了许多GIT命令使用的各种选项和设置。和很多工具一样，GIT支持不同层次的配置文件。按优先级递减的顺序，如下所示：
* .git/config： 版本库特定的配置设置。是默认选项
* ~/.gitconfig：用户特定的配置设置。可用--global选项修改
* /etc/gitconfig： 系统范围的配置设置。

要建立一个作者名和email地址，用于你对**所有版本库**的所有提交，可以使用git config --global命令给在$HOME/.gitconfig文件里的user.name和user.email赋值。

    git config --global user.name "yakamoz"
    git config --global user.email "yakamoz@gmail.com"

如果想设定对**特定版本库**的名字和email地址， 覆盖--global的设置，只需要省略--global标志

    git config user.name "yakamoz"
    git config user.email "yakamoz@gmail.com"

我们也可以设置别名，来代替常用且复杂的GIT命令，如：

    git config --global alias.show-graph 'log --graph --abbrev-commit --pretty=oneline'

当使用git show-graph命令时，就如同已经输入了带所有选项的长长的git log命令一样。

## 增
### 初始化仓
    git init : 把目录变为一个Git版本库，执行命令后， 在此目录中，会有一个.git文件目录。Git会把所有的修改信息保存在这唯一的顶层.git目录里。

### 创建版本库副本
    git clone 源版本库  目的版本库 ： 这里的源版本库可以在本机，也可以存在于网络上

### 新增文件

    git add 文件名： 将文件加入到暂存区中
## 删

    git rm 文件名: 删除文件

## 改
### 重命名文件

    git mv 源文件名  目的文件名

### 改变内容

    git add -A
### 改变提交历史

关于修改历史记录的注意事项：

作为一般原则， 只要没有其他开发人员已经获得你的版本库的副本，你就可以自由地修改和完善版本库提交历史记录。不过要记住一个概念，如果一个分支已经公开了，并且可能已经存在于其他版本库中了，那你就不应该重写、修改或更改该分支的任何部分。

#### git reset
此命令会把版本库和工作目录改变为已知状态。具体而言，git reset 调整HEAD引用指向给定的提交，默认情况下还会更新索引以匹配该提交。可以把git reset 当成“破坏性的“， 因为它可以覆盖并销毁工作目录中的修改。事实上，数据可能会丢失。
#### git cherry-pick
#### git revert



## 查
### 查看修改

    git diff 文件名 ：查看与库上文件的差异

    git diff id1 id2：查看两次提交的差异

    git status　文件目录：查看在此目录下，修改情况

    git blame　文件名：查看该文件每一行最后的修改人信息

    git show id: 查看某次提交的内容, 缺少id时，将会显示最近一次提交的详细信息。

### 查看提交信息

    git log : 查看提交历史信息

## 执行
### 提交
git commit： 前面执行的add, rm 等命令，只是把修改放入到了暂存区，还没有提交到版本库中。 当执行commit命令后， 才会把修改提交到版本库中。一般地，加上 "-m" 选项，表示此次提交的提示信息。如：

    git commit -m "add a file" 

提交到版本库后的每一个对象，均由一个**唯一**的名称，这个名称是根据对象内容应用SHA1得到的SHA1散列值（也就是说，无论文件在哪里，只要文件内容一样，SHA1散列值就相同）。文件的任何变化，均会导致SHA1散列值的不同。

SHA1的值是一个160位的数，通常表示为一个40位的16进制数（如1d136674ddd8608abf951a83c2d6ffc1bd6225b8），有时候，在显示期间，SHA1值被简化成一个较小的、唯一的前缀。Git用户所说的SHA1、散列码和对象ID都是指同一个东西。

### 合并
git merge

解决冲突

## GIT BRANCH

## GIT STASH
    用stash 还是用 cherry-pick。 取决于任务的紧急程度与代码量。
