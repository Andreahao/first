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
		
