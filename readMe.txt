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


	