learn git~
# 初始化一个仓库
git init
# 添加文件
git add readme.txt
# 提交文件
git commit -m "add a readme.txt"

now change readme.txt
# 查看仓库当前的状态
git status
# 查看修改的地方
git diff readme.txt 
# 修改需要提交, 继续git add, git commit

# 版本回退
# HEAD指向当前版本, ^, ~<num>
# 本地 版本回退, 回到过去
git reset --hard commit_id
# 查看提交历史
git log
# 查看命令历史, 确定要移动到的版本,回到未来
git reflog

# git 工作区与暂存区
在进行add时, 是将修改的文件存放在暂存区
commit提交暂存区的内容

# git跟踪管理的是修改,而非文件
# 撤销修改(工作区),将readme.txt文件在工作区的修改撤销,回到最近一次git commit或git add的状态
git checkout -- file [-- 非常重要]
# 将暂存区的修改回退到工作区
git reset HEAD <file> 

#撤销修改小结[前提: 都只是在自己本地代码库中]
场景1: 改乱了工作区某个文件的内容,想直接丢弃工作区的修改内容  git checkout -- file
场景2: 不仅改乱了工作区的文件,还添加到了暂存区,想放弃修改 git reset HEAD file 回到场景1
场景3: 提交到不合适的修改到版本库,要撤销本次提交 git reset commit_id

# 删除文件
git rm file 

# git 与 github
# 添加远程库 [先有本地库,后有远程库时,关联操作]
# 1. github上添加SSH
# 2. 创建repository
# 3. git remote add origin git@github.com:blingyuan/learngit.git [关联一个远程库] 
# 4. git push -u origin master [初次, 远程master上为空, 加上-u参数,git会把本地master推送到origin/master上,并关联]
# 5. git push origin master [之后, 将本地推送到远程 就可以不加-u参数]

# 从远程库克隆 [从零开发, 先创建远程库,然后从远程库克隆]
# 1. 在github上创建repository
# 2. git clone git@github.com:blingyuan/learngit.git [克隆出一个本地库]

# github 支持多种协议, git://使用 ssh , 也支持https协议
# https协议速度慢,每次推送还必须输入口令,但某些公司只开放http端口,就只能使用https



# git 分支
# 一. 创建/合并分支
# 创建dev分支, 切换到dev分支
git checkout -b dev
# 查看当前分支
git branch [*表示当前head的位置]
# 在当前分支进行修改,然后添加到暂存区,提交,切换到主分支,合并,提交到远程分支,删除分支
git add readme.txt;
git commit -m "";
git checkout master; 
git merge dev;  [进行merge时, master分支没有修改, 进行"快速合并/fast forward"]
git push origin master;
git branch -d dev

# 二.解决冲突[进行merge时, master分支有进行过修改, 无法进行"快速合并"]
# 查看冲突文件
1.git status
2.打开冲突文件,解决冲突,重新add并commit
3.git log --graph --pretty=oneline --abbrev-commit[查看分支合并情况]

# 三. 分支管理策略
# fast forword模式下, 删除分支后,会丢失分支信息
# 如果要强制禁用 fast forward模式,git会在merge时重新生成一个新的commit,就可以看出分支信息
1. git checkout -b dev
2. git add readme.txt
3. git commit -m ""
4. git checkout master
5. git merge --no-ff -m "" dev [使用--no-ff禁用fast forward模式,此时merge时要加 -m 描述, 因为是创建一个新的commit]

# 在实际开发中,应该遵循的几个基本原则
# 1. master分支应该是非常稳定的,仅用来发布新版本,平时不能在上面干活
# 2. 每个人有自己dev分支

# 四. Bug分支
# 情景: 当有bug[代号001]产生,此时手上dev分支的readme.txt[之前被git add/git commit过]文件还没修改完,不能进行commit,有个新建的文件 test.txt[没有被git add/git commit过],但是master分支有个紧急bug需要处理,要切换分支
# 情景: 当有bug[代号001]产生,此时手上dev分支的readme.txt[之前被git add/git commit过]文件还没修改完,不能进行commit,有个新建的文件 test.txt[没有被git add/git commit过],但是master分支有个紧急bug需要处理,要切换分支
# 正确步骤:[保留现场]
1. git add test.txt[新建的文件时未被追踪的文件, 需要让他被git追踪]
2. git status [on branch dev, new file: test.txt, modified: readme.txt]
3. git stash [保留现场,saved working directory]
# 切换到需要修复bug的分支,创建对应的bug分支,修复,add, commit, merge,delete
1. git checkout master[在master分支上修复bug]
2. git checkout -b issue-001[创建bug分支, 修复readme.txt文件]
3. git add readme.txt
4. git commit -m "fix bug 001" readme.txt
5. git checkout master
6. git merge --no-ff -m "merge bug 001" issue-001
# bug修复完, 切换到dev分支, 继续工作,恢复
1. git checkout dev
2. git stash list
# 恢复方法
1. git stash apply[恢复后,但内容不删除] + git stash drop[删除stash]
2. git stash pop[恢复的同时删除stash内容]

# 小结: 修复bug时,会通过创建新的bug分支进行修复,然后合并,最后删除
#		当手头工作没有完成时, 先将工作现场git stash一下,然后去修复bug,修复后再git stash pop,回到工作现场

