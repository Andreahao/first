本地仓库

1.创建git仓库
	a. 在空目录下，cmd命令  $ mkdir learngit
							$ cd learngit
							$ pwd(pwd用于显示当前文件的目录)
							
	b. git init 命令把这个目录变成git可管理的仓库
							$ git init

2.将文件提交到仓库
	a. 编写readme.txt文件（注意：不要使用windows自带的记事本编辑，编译出现语法错误。使用Notepad++,设置编码格式UTF-8 without BOM）
	b. 把文件添加到仓库       $ git add readme.txt
	c. 告诉git文件添加到仓库  $ git commit -m '提交说明'（commit之后，index暂存区为空）
		（会提示，改动文件数量、插入内容的行数）
	（$ git commit -a,将当前工作目录同时写到Index缓存区和git仓库）
		
3.文件修改
	a. $ git status 查看仓库当前状态（仓库与本地对比修改文件）
	b. $ git diff 查看修改内容（本地文件与索引文件.git/index文件进行对比）
	   $ git diff HEAD(本地文件与最近一次提交版本进行对比)
	   $ git diff -cache(index文件与最近一次提交版本对比)
	c. 提交修改文件 <1> $ git add readme.txt
					<2> $ git status 再次查看文件状态
					<3> $ git commit -m '提交说明'

4. 版本回退
	a. $ git log 查看提交历史
	b. $ git log --pretty=onelone 查看提交历史版本的id
	c. $ git reset --hard HEAD^ 回退到上一版本（windows7 64位HEAD^^表示回退到上一版本。）HEAD~100回退到前100版本（HEAD指向master的一个指针）
	d. 回退到某一版本
		$ git reset --hard 版本号（版本号不需要全写，前几位就好）
5. 查找之前的命令
	$ git reflog
	
6. .git 隐藏文件（git版本库）
	git版本库存放的内容：
		<1>index文件暂存区；
		<2>git创建的第一个分支master；
		<3>创建指向master的指针HEAD	
			
7.  cat 文件名称		查看文件内容

8.  工作区修改丢弃
	.git checkout file  丢弃工作区的修改
	
9. 缓存区修改丢弃
	.git reset HEAD file
	
10. 删除文件(版本区)
	a. $ .git rm file
	b. $ .git commit -m '描述'
	
11. 误删文件，版本库中还有文件，恢复到最新版本
	git checkout -- file
	
	
远程仓库
1. 创建SSH Key
	SSH,主要用于计算机间加密传输，取代传统的远程登录和远程执行命令工具，实现对远程登录和远程执行命令加密，防止由于网络监听而密码泄露。
	SSH协议是IETF(Internet Engineering Task Force)的Network Working Group所制定的一种协议。
	
	a. 创建SSH Key使用 Git Bash(power shell的一种，window7 自带，若没有需下载，前提是安装.net 4)
	b. $ ssh-keygen -t rsa -c "邮箱地址"
	
	即可在用户主目录user/admine下找到.shll 目录，目录中id_rsa是私钥、id_rsa.pub是公钥。
	
	c. github账户-->settings-->SSH Key-->将id_rsa.pub复制粘贴内容区-->添加SSH成功。

2. 本地git仓库与github远程仓库关联
	本地仓库运行命令 $ git remote add origin git@github.com:@Andreahao/learngit.git
	注意：如果报错，fatal:remote origin already exists.
	(
		<1>先输入 $ git remote rm origin
		<2>再输入 $ git remote add
		<3>再次链接即可
	)
	
3. 本地库内容推送到远程库
	$ git push -u origin maser
		(第一次推送master分支时，加上了-u参数，git不但会把本地的master分支内容推送给远程新的master分支，还会把本地master分支与远程的master分支关联起来。以后推送便不需)
		
4. 从远程库克隆
	找一仓库区，克隆并建本地库 $ git clone git@github.com:Andreahao/hello-word.git
	
分支
	1. 创建分支,并切换到分支
			$ git checkout -b dev
			（git checkout -b 表示，创建并切换。相当于，git branch dev 和 git checjout dev）
	2. 查看分支
			$ git branch(显示全部的分支，当前分支前面有星号*)
			
	dev分支：修改内容-->git add file(添加到缓存区，index文件中)-->git commit -m '备注'（提交到dev分支）-->切换到master分支（git branch master）-->
			git merge dev(将dev分支拉到master分支)
	
	（修复bug-01）
	查看分支合并情况：git log --graph
	
	bug分支：<1>将正在进行的修改“储藏”起来。$ git stash
				($ git status查看修改文件有修改，$ git stash后，再$ git shatus，工作区是干净的没有修改内容，是因为把内容放在某个地方了)
			 <2>切换到有bug分支，在此分支新建一个修复bug的分支issue-01并切换，修复bug后提交到bug分支，切换到master将修复bug后的dev拉到master。
			 <3>找回原先暂存的内容
				
