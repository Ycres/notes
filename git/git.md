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

- 













