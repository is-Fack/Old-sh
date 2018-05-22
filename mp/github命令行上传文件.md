bf95460073ea24925289887c4476c0f39605de61
###创建ssh
	ssh-keygen -t rsa -C "your_email@youremail.com"
找到C盘Users/Administrator/.ssh/id_rsa.pub
###验证ssh
		 ssh -T git@github.com  
###克隆到本地仓库
		 在电脑本地创建一个文件夹，作为本地github的仓库 
		2.将github上的一个仓库进行克隆，这个仓库是我们将要上传文件的目标仓库哦 
		复制github仓库的路径 

		命令
		git clone 路径
		执行命令，然后本地仓库中多了一.个git
		.git是隐藏文件

没多的话
			
		git init(初始化。一切从这里开始)
###设置urername与meail
		 git config --global user.name "your name"  
		 git config --global user.email "your_email@youremail.com"
###添加远程地址
		git remote add origin git@github.com:名字/仓库.git
添加不上的话
		
		git remote rm origin （删除已经添加的远程地址）
		后再试一次
		
###添加  
请保证已经添加远程地址
请保证有README.md这个文件，进到你的本地仓库要添加的库里

		git add 文件名（添加文件到缓存区）
		git commit -m "first commit" （具体不知道、但很关键） 
###再添加到远程仓库里
		$ git push origin master （以后添加用这个）
报错git push报错error: failed to push some refs to 'git@github.com:
		
		git pull --rebase origin master（添加README.md文件）
		git push -u origin master（第一次添加用这个）

###下载别人的代码
		git clone 别人的路径

查看状态码
	git status
如果为红色
	git add .（添加所有文件到缓存区）
	git add '文件'（添加单个文件到缓存区）
如果为绿色说明已经到缓存区，可以直接添加
	
	git pull(拷贝到本地仓库)

上传大的文件时

	git config --global http.postBuffer 157286400 （请求150G的缓存区）

##第二种
