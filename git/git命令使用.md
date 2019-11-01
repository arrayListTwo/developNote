# Git命令使用

> Git是目前世界上最先进的分布式版本控制系统（没有之一）。

## git使用前的设置

* 全局设置名字
	
	```java
	$ git config --global user.name "Your Name"
	```
* 全局设置邮箱

	```java
	$ git config --global user.email "email@example.com"
	```

## git便捷命令
	
* `$ pwd`：显示当前目录
* `$ ls`：当前目录下的所有显示的文件名称
* `$ ls -ah`:当前目录下的所有文件名称(包括隐藏文件)

## git命令使用

* 将目录变成Git可以管理的仓库，此目录文件就是**工作区**
	
	```java
	$ git init
	```
* 将文件添加到仓库,**文件修改添加到暂存区**，使用通配符 * 可以添加此目录下所有未忽略的文件到仓库
	
	```java
	$ git add <filename>
	```
* 将文件提交到本地仓库,**把暂存区的所有内容提交到当前分支**

	```java
	$ git commit -m "本次提交的说明"
	```
* 掌握仓库当前的状态

	```java
	$ git status
	```

* 获取文件修改的具体内容

	```java
	$ git diff
	```
* 显示日志(日期由近及远)

	```java
	$ git log
	```
	* 每一次提交显示一行，可在`$ git log`命令后面加上`--pretty=oneline`参数

* `git diff 948dbb4b eeb99b203f8c8c --name-only`**：**`git diff`这个命令能比较两个提交之间的差异，使用`-–name-only`参数可以只显示文件名。

* 比较两个版本之间的差异

		git diff commit-id-1 commit-id-2 > d:/diff.txt

	结果文件diff.txt中：

    	"-"号开头的表示 commit-id-2 相对 commit-id-1 减少了的内容。
    	"+"号开头的表示 commit-id-2 相对 commit-id-1 增加了的内容。


## 撤销修改文件

* `git checkout -- filename`可以**丢弃工作区的修改**，就是让这个文件回到最近一次`git commit`或`git add`时的状态

	```java
	$ git checkout -- filename
	```

	* 一种是"filename"文件自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态
	* 一种是"filename"已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态

* 命令`git reset HEAD file`可以**把暂存区的修改撤销掉（unstage），重新放回工作区**

## 启动时光机器

> 在Git中，用HEAD表示当前版本，也就是最新的提交

* `HEAD`指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭
	
	* 使用命令`git reset --hard commit_id` ，删除工作空间改动代码，撤销`commit`撤销`git add .` 注意完成这个操作后，就恢复到了commit_id状态。
	
	*  使用命令`git reset --soft commit_id` ，不删除工作空间改动代码，撤销`commit`，不撤销`git add .` ，**此命令可以实现撤销一次commit操作**

	* 使用命令`git reset --mixed commit_id` 或 `git reset commit_id` ，不删除工作空间改动代码，撤销`commit`，并且撤销`git add .` 操作

* 穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本

* 要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本

* `git commit --amend` 命令，修改上一个`commit`注释

## git删除文件

* 确实要删除文件

	* `git rm -f filename` 或者 `git rm -rf dirname` ，同时删除工作区和暂存区的文件
	
	* `git rm --cached filename`， 删除暂存区文件，不删除工作区文件

	* 代码已经`commit`，撤销`commit`，使用`git reset --soft HEAD^`，不删除工作空间改动代码，撤销`commit`，不撤销`add`

## Github远程仓库

* `本地Git仓库`和`GitHub远程仓库`之间的传输是通过`SSH`加密

	```java
	$ ssh-keygen -t rsa -C "youremail@example.com"
	```
	* 此命令运行，可以在用户主目录里找到`.ssh`目录，里面有`id_rsa`和`id_rsa.pub`两个文件，这两个就是`SSH Key`的秘钥对，`id_rsa`是私钥，`id_rsa.pub`是公钥，公钥用于添加到远程仓库的`ssh`

* 已有的一个本地仓库和Github远程仓库关联
	
	```java
	$ git remote add origin 远程仓库地址
	```
	* 远程库的名字就是`origin`
* 把本地库的内容推送到远程，用`git push`命令，实际上是把当前分支推送到远程仓库的某个分支

	```java
	$ git push -u origin master  //首次推送，把本地的分支和远程的master分支关联起来
	```
	```java
	$ git push origin master   //以后推送的简化命令
	```

* 从远程库中克隆一个仓库

	```java
	$ git clone 远程仓库地址
	```

	* 当你从远程仓库克隆时，实际上`Git`自动把本地的`master`分支和远程的`master`分支对应起来了，并且，远程仓库的默认名称是`origin`。
		* 要查看远程库的信息，用`git remote`
		* 用`git remote -v`显示更详细的信息


## 分支管理

> `master`分支是一条线，`Git`用`master`指向最新的提交，再用`HEAD`指向`master`
> `master`分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活

* 创建并切换分支

	```java
	$ git checkout -b 分支名字
	```

	* 创建一个分支
	
		```java
		$ git branch 分支名字
		```
	* 切换到指定分支
	
		```java
		$ git checkout 分支名字
		```
	*
* `git branch`：命令会列出所有分支，当前分支前面会标一个 * 号
* `git merge 分支名字`：命令用于合并指定分支到当前分支
	* 普通模式合并`$ git merge --no-ff -m "本次合并的说明" 分支名称`：合并分支会提交一次commit，故可以查看合并历史
* `git branch -d 分支名字`：命令用于删除指定分支
* **合并冲突**：分支合并的时候会产生冲突，首先需要解决冲突，使用`git add`和`git commit`命令提交代码，代码提交成功则代表分支合并成功
	* 使用`git log --graph`查看合并分支图
	* 使用`git log --graph --pretty=oneline --abbrev-commit`查看合并分支图（**简短**）

## bug修复

* `Git`还提供了一个`stash`功能，可以把当前工作现场**“储藏”**起来，等以后恢复现场后继续工作，被`stash`以后，使用`git status`查看工作分区的状态，应该是干净的。
* 将分支切换到`master`，创建并切换到`bug`分支，在`bug`分支上修复`bug`
* 将分支切换到`master`，合并并删除`bug`分支，`bug`修复完成
* 将分支切换到开发分支`dev`
	* 使用`git stash list`查看储藏列表，恢复工作状态，操作方法如下：
		* 用`git stash apply 储藏索引`恢复，但是恢复后，`stash`内容并不删除，你需要用`git stash drop 储藏索引`来删除；
		* `git stash pop`，此命令会恢复工作状态并删除此索引

## 开发一个新功能

> 开发一个新功能，最好新建一个分支`feature`

* 如果要丢弃一个没有被合并过的分支，可以通过`git branch -D 分支名称`强行删除。

## 推送分支

> 推送分支，就是把该分支上的所有本地提交推送到远程库
> 推送时，要**指定本地分支**，这样，Git就会把该分支推送到远程库对应的远程分支上

* `git push origin master`：推送主分支，master分支是主分支，因此要时刻与远程同步
* `git push origin dev`：推送开发分支

## 版本标记

> `Git` 中使用 `tag` 进行版本标记

> 通过 `Git` 的 `tag` 功能，对生产分支中要发布的提交进行标记

* `Git` 增加 `tag`

```git
$ git tag tagName -m 'tag description'
```

* 删除 `tag`

```git
$ git tag -d tagName
$ git push origin :refs/tags/tagName
```

* 查看 `tag`

```git
git show tagName
```

* 将 `tag` 推到远程仓库

```git
$ git push origin tagName # 推送单个 tag
$ git push origin --tags  # 推送所有的 tag 
```