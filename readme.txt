$ git config --global user.name "sangd"
$ git config --global user.email "sang1989happy@163.com"

因为Git是分布式版本控制系统，所以，每个机器都必须自报家门：你的名字和Email地址。
注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

创建版本库
通过git init命令把这个目录变成Git可以管理的仓库	ls -ah
把文件添加到版本库	
1.用命令git add告诉Git，把文件添加到仓库 git add readme.txt		
2.用命令git commit告诉Git，把文件提交到仓库	git commit -m "wrote a readme file"   -m后面输入的是本次提交的说明


git status  查看文件是否被修改
git diff	查看文件修改的内容

•要随时掌握工作区的状态，使用git status命令。
•如果git status告诉你有文件被修改过，用git diff可以查看修改内容。

HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。
•穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
•要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本


工作区：电脑中能看到的目录，例如 D:\git
版本库：工作区的隐藏目录.git，存了很多东西 例如：stage（暂存区），git自动创建的第一分支master，以及指向master的指针HEAD

前面讲了我们把文件往Git版本库里添加的时候，是分两步执行的：
第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区；
第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。
因为我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改。
你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改

下面，我们要讨论的就是，为什么Git比其他版本控制系统设计得优秀，因为Git跟踪并管理的是修改，而非文件



