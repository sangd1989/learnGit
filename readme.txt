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

下面，我们要讨论的就是，为什么Git比其他版本控制系统设计得优秀，因为Git跟踪并管理的是修改，而非文件。-----
现在，你又理解了Git是如何跟踪修改的，每次修改，如果不add到暂存区，那就不会加入到commit中

场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。
场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库

git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。
命令git rm用于删除一个文件。如果一个文件已经被提交到版本库，那么你永远不用担心误删，但是要小心，你只能恢复文件到最新版本，你会丢失最近一次提交后你修改的内容


远程仓库；
第1步：创建SSH Key  在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步
ssh-keygen -t rsa -C "youremail@example.com"
如果一切顺利的话，可以在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSHKey的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人
第2步：登陆GitHub，打开“Account settings”，“SSH Keys”页面：
为什么GitHub需要SSHKey呢？因为GitHub需要识别出你推送的提交确实是你推送的，而不是别人冒充的，而Git支持SSH协议，所以，GitHub只要知道了你的公钥，就可以确认只有你自己才能推送。在GitHub上免费托管的Git仓库，任何人都可以看到喔（但只有你自己才能改）。
