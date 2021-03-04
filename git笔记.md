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


