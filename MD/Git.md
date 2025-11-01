#                                                                          Git笔记

## 安装和初始化配置

> 打开终端或open git bash here，输入`git -v`查看版本

**使用方式**

- 命令行

- 图形化界面(GUI)

- IDE插件/扩展

1. 配置用户名和邮箱

   `git config --global user.name "xxx"`
   
   `git config --global user.email xxx@qq.com`

2. 保存用户名和密码

   `git config --global credential.helper store`

3. 查看配置信息

   `git config --global --list`

## 新建仓库

1. 新建一个目录`mkdir learn-git`,`cd learn-git`

   `git init`即可创建仓库，出现.git文件，表示该目录是一个被git管理的仓库

2. `git init`后面加文件名，表示新建一个仓库`git init xxx`

3. `git clone 仓库地址`也能创建仓库

## 工作区域和文件状态

- 工作区(working directory)
- 暂存区(staging area/index)
- 本地仓库(local repository)

> 工作区指本地电脑，修改文件后使用`git add`上传到暂存区，再使用`git commit`上传到本地仓库

**文件状态**

![](https://8e7a8eb.webp.li/work/20251101115837136.png)

## 添加和提交文件

- `git init`创建仓库
- `git status`查看仓库的状态
- `git add`添加到暂存区
  - git add .
  - git add *.txt
- `git commit`提交
  - `git commit -m "xxx"`

> Linux命令：echo "文件内容" > 文件名

- `git log`查看提交日志 
  - `git log --online`查看简洁的提交记录

## git reset回退版本

- `git reset --soft`保留工作区和暂存区
- `git reset --hard`两个都不保留
- `git reset --mixed`只保留工作区

## git diff查看差异

- `git diff` 工作区vs暂存区

- `git diff HEAD`工作区+暂存区 vs 本地仓库

- `git diff --cached`暂存区vs本地仓库

  `git diff --staged`暂存区vs本地仓库

- `git diff <commit_hash> <commit_hash>`/`git diff HEAD~ HEAD`

  比较提交之间的差异

- `git diff <branch_name> <branch_name>`比较分支之间的差异

## git rm删除文件

- `rm file` `git add file`先从工作区删除文件，然后暂存删除内容
- `git rm <file>`把文件从工作区和暂存区同时删除
- `git rm --cached <file>`把文件从暂存区删除，但保留在当前工作区中
- `git rm -r *`递归删除某个目录下的所有子目录和文件

## .gitignore忽略文件

- `*`通配任意个字符

- `？`匹配单个字符

- `[]`表示匹配列表中的单个字符，[abc]表示a/b/c
- `**`表示匹配任意的中间目录
- `[0-9]`表示任意一位数字，`[a-z]`表示任意一位小写字母
- `!`表示取反 

##  ssh配置和克隆仓库

- `cd.ssh`

- `ssh-keygen -t rsa -b 4096`

> 私钥文件：id_rsa
>
> 公钥文件：id_rsa.pub
>
> 将公钥添加到GitHub

 `git pull`

`git push`

 







