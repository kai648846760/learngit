## 安装
+ Linux
```
$ git
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git
```
+ windows
 ```
 安装包安装即可（https://git-scm.com/downloads）
 ```

+ 安装完成后设置配置
```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

## 创建版本库
```
#先创建一个目录或引用一个目录
$ mkdir learngit
$ cd learngit
$ pwd
/Users/michael/learngit

#通过git init命令把这个目录变成Git可以管理的仓库：
$ git init
Initialized empty Git repository in /Users/michael/learngit/.git/
#瞬间Git就把仓库建好了，而且告诉你是一个空的仓库（empty Git repository）
```

### 添加文件到Git仓库(2步曲)
1. git add <file>
2. git commit -m <message>

> file必须要在仓库内，简单解释一下git commit命令，-m后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。
+ 示例
```
#编写一个readme.txt文件，内容如下：

Git is a version control system.
Git is free software.

#第一步，用命令git add告诉Git，把文件添加到仓库：

$ git add readme.txt

#第二步，用命令git commit告诉Git，把文件提交到仓库：

$ git commit -m "wrote a readme file"
[master (root-commit) eaadf4e] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```

#### 为什么Git添加文件需要add，commit一共两步呢？
+ 因为commit可以一次提交很多文件，所以你可以多次add不同的文件，比如：
```
$ git add file1.txt
$ git add file2.txt file3.txt
$ git commit -m "add 3 files."
```

## 时光穿梭机
+ 要随时掌握工作区的状态，使用git status命令。
+ 如果git status告诉你有文件被修改过，用git diff可以查看修改内容。

### 版本回退
+ git log命令显示从最近到最远的提交日志，我们可以看到3次提交，如果嫌输出信息太多，看得眼花缭乱的，可以试试加上--pretty=oneline参数
+ $ git reset --hard HEAD^ 回到上一个版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
+ $ git reset --hard <id> 回退至指定版本
+ git reflog 可查看回滚操作记录


### 工作区-暂存区
+ 工作区（Working Directory）
就是你在电脑里能看到的目录，比如我的learngit文件夹就是一个工作区

+ 版本库（Repository）
工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。
Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。

### 管理修改
+ 每次修改，如果不用git add到暂存区，那就不会加入到commit中。

### 撤销修改
+ 场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file / git restore <file>

+ 场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。 或者使用 git restore --staged <file>，然后再用git restore <file>

+ 场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库
### 删除文件
+ 命令git rm用于删除一个文件。如果一个文件已经被提交到版本库，那么你永远不用担心误删，但是要小心，你只能恢复文件到最新版本，你会丢失最近一次提交后你修改的内容

## 远程仓库
### 添加远程库
```
#1、添加库
$ git remote add origin <地址>
例：$ git remote add origin git@github.com:kai648846760/pytest--Chinese.git

#2、本地库的所有内容推送到远程库上
$ git push -u origin master
#此后推送，只需要输入git push origin master即可

```
### 远程库克隆
+ 要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。

+ Git支持多种协议，包括https，但ssh协议速度最快。

## 创建于合并分支
+ 查看分支：git branch

+ 创建分支：git branch <name>

+ 切换分支：git checkout <name>或者git switch <name>

+ 创建+切换分支：git checkout -b <name>或者git switch -c <name>

+ 合并某分支到当前分支：git merge <name>

+ 删除分支：git branch -d <name>