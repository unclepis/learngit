Git is a distributed version control system.
Git is free software distributed under the GPL.

使用超级管理员权限安装插件：
sudo cnpm install -g xxx
在全局环境下安装xxxx

learngit(工作区)－－>.git(版本库)，版本库里面有缓存区和master分支。

－－－－－－－－－在本地创建仓库－－>托管到远程仓库－－－－－－－－－－－
	1>mkdir repostory_name／／创建本地仓库
	2>cd repostory_name//切换到当前仓库
	3>pwd ／／查看路径
	4>在本地仓库里面创建文件，比如readMe.txt
	5>修改文件并add commit
		git add readMe.txt	//添加到缓存区stage
		git commit -m"desc"	／／提交到master分支
	6>git init   //初始化仓库，创建仓库的版本库.git
	7>手动在远程git上创建仓库
	8>创建联系
		git remote add origin git@github.com:uncliepis/learngit.git
	9>在本地修改文件，add并commit
	10>git push origin master
		//将本地文件push到远程库
		／／可以是master库也可以是别的库
－－－－－－－－－－－－－－－－－－－－－－－－－－－－－－－－－－－－－－
1.create the repository创建版本库
	mkdir folder name    //create the repository
		在本地创建仓库
	cd folder name      //access the path of the folder
		切换到仓库
	pwd                 //public work department,show the current path of folder
2.initial the git repository 
	git init	//initialised empty git repository
			／／把这个目录变成了git可以管理的版本库
			／／.git目录是git涌来跟踪管理版本库的，不要随意更改。
	<how to add a file into repository>往git版本库里面添加东西
		-git add把文件添加到缓存区。
		-git commit把缓存区的所有内容提交到当前分支。

3.add the new plain file
	git add filename	//tell Git to add the file in repository
4.commit the file
	git commit -m “describe the modification”	//tell Git submit the file in repository

	<check the modification>
		-git status	//whether or not the file modified
		-git diff	//check the difference if the status show the file was modified
		-cat filename	//show the content of the file

5.check the content of file
	cat filename
	vi filename //打开或新建文件
	:wq保存并退出
6.check the status of the file
	git status	//check the current status of the repository
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

	git checkout - - file  //撤销工作区的文件／／没有add也没有commit
		git checkout branchName//切换到分支
	git reset HEAD file	//撤销缓存区的文件	／／已经add
	git reset HEAD commit_id//版本回退 //已经commit

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

14.分支管理
1>一开始的时候，git只有一个主分支master，每次提交一次，master往前移动一次，HEAD指向master，master指向最新的提交。
2>当我们创建新的分支，git新建一个指针叫dev，指向master相同的提交，再把HEAD指向dev，就表示当前的分支在dev上。
3>我们在dev上的工作完成了，就可以把dev合并到master上，合并完以后甚至可以删除dev分支。
	git checkout -b dev	//创建了dev分支，并且把HEAD指向dev
		-b表示创建并切换
		git branch命令会列出所有分支，并在当前分支前面加＊
	git commit -m ”newCommit” //发生了新的提交，dev分支发生移动，HEAD指向dev也发生移动。
	git checkout master	//切换回master分支
	git merge dev	//合并dev到master主分支
		git merge命令用语合并指定分支到当前分支。
	git branch -d dev	//删除dev分支

小结：git鼓励大量食用分支：
查看分支：git branch
创将分支：git branch name
切换分支：git checkout name
创建并切换分支：git checkout -b name
合并某分支到当前分支：git merge name
删除分支：git branch -d name

15.conflict解决冲突
当git无法自动合并分支的时候，就必须首先解决冲突，然后再提交合并结果。
	创建并切换分支：git checkout -b feature1
		在feature1上改变文件：-do something changes in the files
		提交到缓存区：git add file
		提交到该分支：git commit -m ”comment”
	切换到原来的分支:git checkout master(系统会提示当前的分支比远程分支库提前一个提交，因为还没有同步到远程库)
		在master上改变文件：
		提交到缓存区域：
		提交到master分支：
//到这，feature1和master分支文件都发生了更改。在这种情况下，git没法执行快速合并f。
	自动合并分支:git merge feature1
//git会提醒你发生了冲突，必须手动解决冲突；通过git status可以查看冲突的文件
//git会用<<<<<<<<<<<,=========,>>>>>>>>标记处不同分支的内容

	需要修改发生冲突的文件，并使的他们有一致的内容。
	提交到缓存区域
	提交到分支
	合并两个分支git merge feature1;此时合并完成。
	删除分支 git branch -d feature1

简单的说就是当两个分支发生冲突的时候，不能尽兴fast forward快速合并，需要手动的修改发生冲突的文件，统一之后再合并。

使用git log可以查看分支的合并图。

16.分支管理策略
通常，合并分支时，git会使用ff(fast forward)模式，但是删除分支后，会丢失分支信息。
所以如果要禁止ff模式，git就回在合并merge的时候生成一个新的commit，这样从分支历史上就可以看出分支信息。

	创建并切换分支：git checkout -b dev
	修改dev分支上的文件
	添加到缓存去
	提交到dev分支
	切换到master分支 git checkout master
	合并dev分支并禁用ff模式：git merge — -no-ff -m”merge with no-ff” dev

17.分支管理策略：
1>master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在这分支上干活。
2>新建一个dev分支，在这干活，然后在这个dev上的版本稳定需要发布的时候，把dev分支合并到master上发布。
3>每个人都在自己的分支上工作，然后是不是往dev分支上合并就好了，然后等最后的dev完成需要发布，合并到master上。
普通模式:- -no-ff合并后的历史有分支信息
快速模式：fast forward合并后没有分支信息。

18.bug分支
当修复bug的时候我们会创建一个分支进行修复，然后合并并删除该分支。
当手头工作没有完成的时候，先把工作现场git stash一下，然后去修复bug，修复后在git stash pop回到工作现场。

在master分支下创建了一个dev分支正在修改项目，突然临时接到任务，需要修改一个bug，所以创将了一个issue-01分支来修改bug，但是之前的dev分支上的任务还没有完成，所以需要临时存储着歌dev分支的修改，但是不提交并合并到master。

	git stash	//临时存储当前的工作区
	git status	//存储了当前工作区后查看工作区是干净的，没有发生修改。
		git checkout master	//回到master分支
		git checkout -b issue-01	／／创建并切换到issue-01分支准备修改bug
		修改bug文件bugs
		git add bugs
		git commit -m”fix bugs”
	//可以返回master然后合并issue-01分支
	//也可以直接把master分支合并到issue-01分支.(git checkout master或者可以把修复的bug issue-01分支合并到master)
	git checkout master	//切换会master分支
		
	git merge — -no-ff -m”bugs information” issue-01 //合并issue-01分支到master分支
	git branch -d issue-01	／／删除了修复bug的issue-01分支
	git checkout dev	／／返回到上一个任务分支dev
		git stash list 	／／可以查看上一个任务存储列表
／／恢复上一个任务的工作区两种方法：

	1>git stash apply	//恢复上一个任务的工作区，但是stash内容不删除
		git stash drop／／删除stash内容
	2>git stash pop	//恢复的同时把stash内容页删除了

19.feature 分支
当创建了一个feature分支，在没有被合并到其他分支的前提下需要删除，则需要使用git branch -D feature01
	
一般的git上master上是作为版本更新的分支，要修改需要使用创建一个dev分支，然后每个人开发一个feature分支。feature分支开发完成提交到dev分支，最后合并到master分支发布。
	//一般的流程就是创建feature01分支，实现功能，合并到dev分支，删除feature01分支
	git checkout -b feature01;
		开发功能fun
	git add fun
	git commit -m”function”
	git checkout dev
	git merge - -no-ff -m”function describe” feature01;
	git branch -d feature01

	／／实际情况是
	git checkout -b feature01;
		开发功能fun
	git add fun
	git commit -m”function”
	git checkout dev
在此时，接到上级命令，新功能发布取消。需要删除feature01分支不合并到dev中。
	由于feature01分支创建并作了修改，但是还没有合并到其他分支里面，git会提示，该分支没有被合并，如果删除将会丢失修改，如果强行需要删除，则需要使用
	git branch -D feature01;
此时没有被合并的feature01分支被强行删除了。

20.多人协作
工作模式：
	1>首先，git push origin branchName推送自己的修改
	2>如果推送失败了，则因为远程分支比你的本地更加的新，所以需要使用git pull试图合并。	
		如果git pull提示no tracking information则说明本地分支和远程分支没有建立关联。
		需要使用git branch - -set-upstream branchName origin/branchName建立关联。
	3>如果合并有冲突，则解决冲突，并在本地提交
	4>如果没有冲突或者解决了冲突，再用git push origin branchName推送就能成功。
	
git remote ／／查看远程库的信息
git remote -v	／／查看远程库的详细信息
git push origin branchName	//将本地的branchName推送到远程的origin/branchName
	推送失败，显示远程库比本地库版本更加的新，则使用git pull抓取远程版本内容。
git checkout -b branchName origin/branchName	／／创建本地仓库，并准备和远程库建立关联
git branch - -set-upstream branchName origin/branchName	//建立本地库和远程库的关系
git pull	／／从远程抓取分支，如果有冲突解决冲突。

21.标签管理
发布一个版本的时候，我们需要在版本库中打一个标签，这样就为宜确定了大标签的版本，无论身时候，取出这个标签的版本，就可以把那个大了标签的时候的历史版本取出来。

git的标签就是指向某个commit的指针。由于commit的id是一串字符串不好记忆。所以标签就是一个让人容易记住的有意义的名字，它跟commit绑定在一起。

22.创建标签：
1>切换到需要打标签的分支上
git branch	／／查看所有分支信息
git checkout master	//切换到需要发布的master分支
git tag name	／／创建了一个新标签
git tag		／／查看所有的tag标签

//默认的标签是打在现在分支的最后提交的commit id上（HEAD）。
//如果忘记打标签了,可以使用git log查看日志找到相关的commit id然后打上标签。

git tag v3.0 commit_id	//这样就把commit——id打了v3.0的标签

／／标签的顺序不是按照时间顺序，而是按照字母顺序。
git show tagName	／／查看标签信息，包括commit_id，date，author，commitName
git tag -a tagName -m”description” commit_id	//－a指定标签名，－m添加文字说明

23.操作标签
git push origin tagName	//推送一个本地标签
git push origin - -tags	//可以推送全部为推送哟的本地标签
git tag -d tagName	//删除一个本地标签
git push origin :refs/tags/tagName	//可以删除一个远程标签。

24.使用github
在github上，可以任意的fork开源仓库
	然后clone到本地
自己用用fork后的仓库的读写权限
可以推送pull request给官方库来贡献代码

25.忽略特殊文件
把不想提交的在git版本库目录下的文件隐藏到.gitingore下。



