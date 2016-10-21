Git is a distributed version control system.
Git is free software distributed under the GPL.

1.create the repository
	mkdir folder name    //create the repository
	cd folder name      //access the path of the folder
	pwd                 //public work department,show the current path of folder
2.initial the git repository 
	git init	//initialised empty git respository

	<how to add a file into repository>往git版本库里面添加东西
		-git add把文件添加到缓存区。
		-git commit把缓存区的所有内容提交到当前分支。

3.add the new plain file
	git add filename	//tell Git to add the file in respository
4.commit the file
	git commit -m “describe the modification”	//tell Git submit the file in repository

	<check the modification>
		-git status	//whether or not the file modified
		-git diff	//check the difference if the status show the file was modified
		-cat filename	//show the content of the file

5.check the content of file
	cat filename
6.check the status of the file
	git status	//check the current status of the respository
7. check the difference between the two modification
	git diff	//tell user the modification 
	<how to go back or go to the target edition of the Git>
		-git reset - -hard commit_id.	//just input the first few numbers of commit_id
		-git reset - -hard HEAD.
			//HEAD 	current commit
			//HEAD^	previous commit
			//HEAD^^ The previous before commit.
			//…
			//HEAD~100 the 100 previous commit.
		-git log	//check the history commit,in order to go back.
		-git reflog    //check the command history,in order to go to the target edition.


8.working directory:（工作区）
	-repository(.git)版本库
		-stage(缓存区)
		-master branch
			－HEAD(当前commit)
9.在工作区修改了文件－－>使用git.add将工作区的文件添加到版本库的缓存区中－－>使用git.commit将缓存区的文件提交到当前版本。

1>当只是修改了工作去的文件，并没有添加到缓存区：git checkout - - file.撤销工作区的修改
2>在工作区修改了文件，并添加到了缓存区，但海没有提交到当前版本分支：git reset HEAD file可以把缓存区的修改撤销，并重新放回工作区。然后再使用git checkout - - file撤销工作区的修改。
3>修改了工作去文件，也添加到了缓存，还进行了提交，使用git reset HEAD commit_id返回上一个commit。

10.delete file
1>在目录文件夹下直接删除或者使用rm file的命令就行删除。
2>这个时候工作区和版本库不一致了。
	－确定也要从版本库里面删除文件
		git rm file
		git commit -m “remove file”.
	-工作区删除错了，从版本库恢复文件
		git checkout － － file.

11.远程仓库
本地的git仓库和gitbub仓库之间的传输是通过ssh加密的
1>创建ssh key
ssh-keygen -t rss -C “youremail@example.com”
在.ssh目录下有一个私钥和一个共钥文件：
id_rsa 这个是私钥，不能公开出去
id_rsa.pub这个是公钥，可以放心地告诉任何人。

2>登陆gitbub在account settings里面添加ssh key，点击add ssh key，填上任一的title，在key文本框里面粘贴id_rsa.pub文件的内容。

3>这样gitbub就可以识别出你推送的提交确实是你自己推送的，而不是别人冒充的，而git支持ssh协议。所以，gitbub只要知道了你的公钥，就可以确定只有你自己才能推送。

4>gitbub允许添加多个key，这样如果你有多个电脑，比如一会在公司，一会在家提交，只需要把每台电脑的key都添加带gitbub上，这样就好了。

5>gitbub上免费托管的git仓库，任何人都可以看到，除非交费把它变成私有仓库，或者自己搭建一个git服务器。


	