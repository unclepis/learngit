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

	<先创将本地仓库－－>数据同步到远程仓库>
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

12.添加远程仓库
在本地意境创建了一个git仓库，想在github上也创建一个远程git仓库，完成两个库远程同步。
	这样github上的仓库可以作为备份
	也可以协助其他人通过该仓库进行协作。
1>create a new repository
2>repository name和本地的git库名字一致。
3>在本地仓库下运行 git remote add origin git@github.com:userName/repositoryName.git
	origin是远程库的名字
	userName为github的账号
	repositoryName为本地git仓库的名字
4>把本地库的所有内容推送到远程库上：
	git push -u origin master
		git push	//把当前分支master推送到远程
		－u  //在第一次推送，把本地master分支内容推送到远程新的master分支
		    //在本地master分支和远程的master分支之间创建关联，方便以后推送。
	以后的本地推送: git push origin master

	<先创将远程仓库－－>从远程仓库克隆到本地>
13.从远程库克隆
1>在github上创将一个仓库
2>创将仓库的名字repositoryName,勾选使用readMe.md初始化这个仓库。
3>git clone git@github.com:userName/repositoryName.git
4>切换到克隆的仓库 cd repositoryName
5>ls指令输出所有的子目录文件，查看有没有readMe.md文件
6>多人协作的项目，每个人克隆一份就好了。
7>在本地克隆仓库或者建立远程仓库，需要知道仓库的地址。默认的ssh使用git://，使用https://也是可以的。git支持多种协议，包括https。在添加仓库地址的时候，可以使用https或者ssh，因为ssh支持的原成git协议速度最快，但是有的公司只开放https端口的公司就只能用这个，不能用ssh协议。


	