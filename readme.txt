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

# HEAD指向当前版本, ^, ~<num>
# 本地 版本回退, 回到过去
git reset --hard commit_id
# 查看提交历史
git log
# 查看命令历史, 确定要移动到的版本,回到未来
git reflog
