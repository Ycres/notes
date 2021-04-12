### 安装git

- 在**Linux**上安装

  ```
  sudo apt-get install git
  sudo apt-get install git-core
  ```

- 在**Windows**上安装

  在[git官网](https://git-scm.com/downloads)上下载

  > 安装完成后，在开始菜单里找到“Git”->“Git Bash”

  ```
  $ git config --global user.name "Your Name"
  $ git config --global user.email "email@example.com"
  ```

### 创建版本库

- 初始化git

  ```
  $ git init
  ```

  

- 文件添加到仓库

  ```
  $ git add filename
  ```

  

- 提交添加文件到仓库

  ```
  $ git commit -m pscontent
  ```

  

  > -m 后面添加说明

### 时间版本管理

#### 版本回退

- ``git log ``查看历史记录

- ```git log --pretty=oneline```

- ```git reset --hard HEAD^```

  > 回退上一版本。
  >
  > 当前版本为```HEAD```，上一版本为`HEAD^`,上上版本为```HEAD^^```,......
  >
  > 如果要回退前100版本，可写为```head~100```

- `git reset --hard CommitId`其中CommitId只需要前几位
- `git reflog`用于记录命令，可寻找CommitId

#### 工作区和暂存区

- 工作区(working Directory)

  > 电脑中能看到的目录

- 版本库(Repository)

  > 工作区的隐藏目录`.git`
  >
  > `stage`/`index`暂存区
  >
  > Git自动创建的第一个分支`master`以及指向`master`的一个指针`HEAD`

- `git status`查看状态

- 总结：

  > `git add` ：把修改提交到暂存区(`stage`/`index`)
  >
  > `git commit`：把修改提交到分支

#### 管理修改

- **注意** `git commit`只负责提交暂存区的修改
- `git diff HEAD -- filename`查看工作区和版本库里最新版本的区别

#### 撤销修改

- `git checkout -- filename`可以丢弃工作区的修改

- `git reset HEAD <file>`可以把暂存区的修改撤销掉(unstage)

- 提交到版本库，应用版本回退

### 远程仓库

#### 一些设置

> 1、创建SSH Key。在用户主目录下(`cd ~`)，看看有没有.ssh目录，如果有，再看看这个目录下有没有`id_rsa`和`id_rsa.pub`这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：
>
> ```ssh-keygen -t rsa -C youremail@example.com```
>
> 其中，`id_rsa`是私钥，id_rsa.pub是公钥
>
> 2、登陆GitHub，打开“Account settings”，“SSH Keys”页面，然后，点“Create SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容

#### 添加远程库

- > `git remote add origin git@github.com:username/repositoriesname.git`
  >
  > 其中远程仓库的名字为origin，可以改名为别的

- 把本地库推送到远程库上

  > `git push -u origin master`
  >
  > -u可不加

- 删除远程库

  > `git remote -v`
  >
  > 查看远程库信息

#### 从远程库克隆

- > `git clone git@github.com:ycres/repositoriesname.git`

### 分支管理

#### 创建与合并分支

- 创建分支

  > `git checkout -b dev`
  >
  > `-b`参数表示创建并切换，相当于
  >
  > `git branch dev`
  >
  > `git checkout dev`

- `git branch`查看当前分支，当前分支前面会标*

- `git merge dev`

  > 把`dev`的分支成果合并到`master`上

- `git branch -d dev`

  > 可以删除dev分支

- 切换分支`git checkout <name>`，`git switch <name>`

#### 解决冲突

- `git switch -c feature`
- git用`<<<<<`，`=======`，`>>>>>>>`标记出不同分支的内容
- `git log --graph --pretty=oneline --abbrev-commit`可以看到分支的情况

#### 分支管理策略

- `git merge --no-ff -m "merge with no-ff" dev`

- > 合并分支时，`--no-ff`参数可以用普通模式合并，合并后的历史有分支，`fast forward`合并看不出曾经做过合并

#### Bug分支

- `git stash`

  > 储存工作现场

- `git checkout master`

- `git stash list`

  > 查看工作现场

- `git stash apply`，`git stash drop`

  > 回复工作现场，并删除stash中的内容

- `git stash pop`

  > 之前上述两种操作

- `git stash apply stash@{0}`指定恢复`stash`

- `git cherry-pick <commit>`复制一个特定的提交到当前分支

#### Feature分支

- 删除分支`git branch -d feature-vulcan`如果未合并会销毁失败
- `git branch -D feature-vulcan`强行删除需要加`-D`参数

#### 多人协作

- `git remote`查看远程库信息
- `git remote -v`查看更详细信息

- `git push origin branch-name`如果推送失败，先用`git pull`抓取远程新提交
- 在本地创建和远程对应的分支关联，使用`git checkout -b branch-name origin/branch-name`
- 使用`git branch --set-upstream branch-name origin/branch-name`建立和远程分支的关联

#### Rebase

- `git rebase`可以把本地未push的分叉提交历史整理为直线

### 标签管理

> tag 是一个容易让人记住的有意义的名字，跟某个commit绑在一起

#### 创建标签

- 首先切换到需要打标签的分支`git checkout branch-name`
- `git tag v1.0`
- `git tag`查看所有标签
- `git tag v0.9 commitId`
- `git show <tagname>`查看标签信息
- `git tag -a v1.0 -m "..." commitId`其中，`-a`指定签名，`-m`指定说明文字

#### 操作标签

- 删除标签`git tag -d v0.1`
- `git push origin v1.0`推送某个标签到远程
- 一次性推送全部尚未推送到远程的本地标签`git push origin --tags`
- 从远程删除标签`git tag -d v0.9`先从本地删除，然后`git push origin :refs/tags/<tagname>`

### Gitee

> 国内Git托管服务[Gitee](gitee.com)

暂略

### 自定义Git

- 让Git显示颜色

  > `git config --global color.ui true`

#### 忽略特殊文件

略

#### 配置别名

略

#### 搭建Git服务器

- 准备一台运行Linux的机器

- 安装`git`

  > `sudo apt-get install git`
  >
  > CentOS用yum安装

- 创建一个git用户，用来运行`git`服务

  > `sudo adduser git`

- 创建登录证书

  > 搜集需要登录的用户的公钥，即`id_rsa.pub`，把所有公钥导入到`/home/git/.ssh/authorized_keys`文件中，一行一个

- 初始化Git仓库

  > - 先选定一个目录作为Git仓库，在该目录下输入命令`sudo git init --bare sample.git`。服务器上的Git仓库通常是以`.git`结尾
  > - 把owner改为`git`：`sudo chown -R git:git sample.git`

- 禁用Shell登录

  > 通过编辑`/etc/passwd`完成，找到
  >
  > `git:x:1001:1001:,,,:/home/git:/bin/bash`改为
  >
  > `git:x:1001:1001:,,,:/home/git:/usr/bin/git-shell`

- 克隆远程仓库

  `git clone git@server:/svr/sample.git`

- 管理公钥

  > 把每人的公钥搜集起来放到服务器的``/home/git/.ssh/authorized_keys``











