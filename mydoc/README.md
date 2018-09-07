# git 指令
-------------------------
## 配置
	$ git config --global user.name "Your Name"
	$ git config --global user.email "email@example.com"

Your name: **github 账号**

email@example.com : **注册 github 的邮箱**


##配置秘钥 ssh-keygen

> 生成秘钥

	1. $ ssh-keygen -t rsa -C "youremail@example.com"

> 测试秘钥是否成功

	2. ssh-T git@github.com		测试是否成功
	

## 常用指令

	$ git init		初始化仓库
	$ git status 	获取状态
	$ ls -ah		显示隐藏文件
	$ git add file		file和后缀名都要写
	$ git add *		全部添加
	$ git commit -m "提交说明"		提交文件
	$ git remote add origin git@github.com:jessie-zly/-.git		关联自己GitHub上的仓库
	$ git push -u origin master		推送文件到github
	
	$ git push origin master	

	$ git fetch origin master 从远程仓库获取最新版本到本地

	$ git merge origin/master 把远程下载下来的代码合并到本地仓库

	$ git clone git@github.com:账号/仓库名.git



## 删除本地仓库

	 $ find . -name ".git" | xargs rm -Rf

> **即删除本地仓库中的.git文件夹**
	
	


# git使用时出现的问题
------------

	1. $ git push -u origin master
		To github.com:jessie-zly/DevelopSoftware.git
		 ! [rejected]        master -> master (fetch first)
		error: failed to push some refs to 'git@github.com:jessie-zly/DevelopSoftware.git'
		hint: Updates were rejected because the remote contains work that you do
		hint: not have locally. This is usually caused by another repository pushing
		hint: to the same ref. You may want to first integrate the remote changes
		hint: (e.g., 'git pull ...') before pushing again.
		hint: See the 'Note about fast-forwards' in 'git push --help' for details.

原因:

**GitHub远程仓库中的README.md文件不在本地仓库中**

解决方案:

执行
	
	git pull --rebase origin master

再执行

	git push -u origin master


---------------------
# git指令
----------------
##全局配置
>`$  git config --global user.name "<username>"`
> 
>`$  git config --global user.email "<email>"`
>
> >--global是全局进行配置
 
##配置秘钥

> 生成秘钥:

> `$ ssh-keygen -t rsa -C "<email>"`

> 测试秘钥是否成功

> `$ ssh-T git@github.com`

> ##配置ignore文件

> 仓库 的根目录下

> 创建`.gitignore`文件

> 忽略`add`进暂存区的文件/文件格式

> * `/文件夹名/`或者`/文件名/`

> 不忽略某个文件夹/文件

> * `!/文件夹名/`或者  `!/文件/`

## 常用指令
>
* `$ git init`    初始化仓库,在文件夹下git bash
* `$ git status`  获取状态
* 
* `$ ls -ah`  显示隐藏文件
* `$ git add file`   文件名和后缀名都要写
* 
* `$ git commit -m "备注"`  提交文件,并且加上注释
* `$ git remote add origin 仓库地址` 给本地repository关联远程地址
* 
* `$ git push -u origin master`  第一次推送文件到远程仓库
* `$ git push origin master`  之后的推送
* 
* `$ git fetch origin master`  从远程仓库`origin`的`master`分支获取最新版本到本地
* `$ git merge origin/master` 把远程的`origin`下载的代码合并到本地仓库
* 
* `$ git pull origin master` 等价于`git fetch `+`git merge`
* `$ git clone git@github.com:hubary/javascript.git`  克隆仓库


## 查看指令
>
* `$ git status`
* `$ git diff`  -----difference
* `$ git log`  显示从最近到最远的提交日志--pretty==oneline----4eds6udhsi----->是版本commit ID
* `$ git reflog`  记录的每一次命令

##版本回退
> 
* `$ HEAD` 表示当前版本
* `$ HEAD^` 表示上一个版本
* `$ HEAD^^` 表示上上一个版本
* `$ HEAD~100` 表示上100个版本
* 
* `$ git reset --hard HEAD^`  回退上一个版本
* `$ git reset --hard 2e323e4`  ----->可以不全

## 删除本地仓库
> `$ find . -name ".git" | xargs rm -Rf`
> 删除本地仓库的.git文件夹

##分支管理
> 
* `$ git branch`  查看分支
* `$ git branch <branchname>`  创建分支
* 
* `$ git checkout <branchname>`  切换分支
* `$ git checkout -b <branchname>`   创建并且切换到该分支
* 
* `$ git merge <branchname> `  合并分支到当前分支
* `$ git merge --no--ff -m "备注"`  合并分支,并添加"commit信息"
* 
* `$ git branch -d <branchname>`  删除分支
* `$ git branch -D <branchname> ` 强行删除分支
* 
* `$ git log --graph`  查看分支合并情况
* `$ git log --graph --pretty=oneline --abbrev-commit`  查看分支合并情况(好看点)
* 
* `$ git checkout -b <branchname><responsename>/<branchname>`创建远程origin的branch分支到本地
* `$ git branch --set-upstream <branchname> origin/<branch-name>`建立本地分支和远程分支 的链接,之后再次 git pull
* 
##工作区
>
> `$ git status` 查看工作区
> `$ git stash` debug项目时暂存工作区内容
> `$ git stash list`查看工作区存储
> >`$ git stash apply`恢复工作区,但是stash内容不删除
> >`$ git stash drop`删除工作区的内容
> `$ git stash pop`恢复并删除

##多账户同时关联
> `$ git remote` 远程库信息
> `$ git remote -v`查看本地库链接的详细远程库的信息
> `$ git remote add github 远程仓库地址`
> `$ git remote add gitee 远程仓库地址`
>>> 仓库名称要有区别,默认origin,但是有冲突的时候就要单独取名
>>> 推送到github
>>> `$ git push github master`
>>> `$ git push gitee master`
    