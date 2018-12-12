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
# 1. github上添加SSH
# 2. 创建repository
# 3. git remote add origin git@github.com:blingyuan/learngit.git [关联一个远程库] 
# 4. git push -u origin master [初次, 远程master上为空, 加上-u参数,git会把本地master推送到origin/master上,并关联]
# 5. git push origin master [之后, 将本地推送到远程 就可以不加-u参数]