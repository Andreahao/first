1.创建git仓库
	a. 在空目录下，cmd命令  $ mkdir learngit
							$ cd learngit
							$ pwd(pwd用于显示当前文件的目录)
	b. git init 命令把这个目录变成git可管理的仓库
							$ git init

2.将文件提交到仓库
	a. 编写readme.txt文件（注意：不要使用windows自带的记事本编辑，编译出现语法错误。使用Notepad++,设置编码格式UTF-8 without BOM）
	b. 把文件添加到仓库       $ git add readme.txt
	c. 告诉git文件添加到仓库  $ git commit -m '提交说明'
		（会提示，改动文件数量、插入内容的行数）
		
3.文件修改
	a. $ git status 查看仓库当前状态（仓库与本地对比修改文件）
	b. $ git diff 查看修改文件中的修改的内容
	c. 提交修改文件 <1> $ git add readme.txt
					<2> $ git status 再次查看文件状态
					<3> $ git commit -m '提交说明'

	