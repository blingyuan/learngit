learn git~
# ��ʼ��һ���ֿ�
git init
# ����ļ�
git add readme.txt
# �ύ�ļ�
git commit -m "add a readme.txt"

now change readme.txt
# �鿴�ֿ⵱ǰ��״̬
git status
# �鿴�޸ĵĵط�
git diff readme.txt 
# �޸���Ҫ�ύ, ����git add, git commit

# �汾����
# HEADָ��ǰ�汾, ^, ~<num>
# ���� �汾����, �ص���ȥ
git reset --hard commit_id
# �鿴�ύ��ʷ
git log
# �鿴������ʷ, ȷ��Ҫ�ƶ����İ汾,�ص�δ��
git reflog

# git ���������ݴ���
�ڽ���addʱ, �ǽ��޸ĵ��ļ�������ݴ���
commit�ύ�ݴ���������

# git���ٹ�������޸�,�����ļ�
# �����޸�(������),��readme.txt�ļ��ڹ��������޸ĳ���,�ص����һ��git commit��git add��״̬
git checkout -- file [-- �ǳ���Ҫ]
# ���ݴ������޸Ļ��˵�������
git reset HEAD <file> 

#�����޸�С��[ǰ��: ��ֻ�����Լ����ش������]
����1: �����˹�����ĳ���ļ�������,��ֱ�Ӷ������������޸�����  git checkout -- file
����2: ���������˹��������ļ�,����ӵ����ݴ���,������޸� git reset HEAD file �ص�����1
����3: �ύ�������ʵ��޸ĵ��汾��,Ҫ���������ύ git reset commit_id

# ɾ���ļ�
git rm file 

# git �� github
# ���Զ�̿� [���б��ؿ�,����Զ�̿�ʱ,��������]
# 1. github�����SSH
# 2. ����repository
# 3. git remote add origin git@github.com:blingyuan/learngit.git [����һ��Զ�̿�] 
# 4. git push -u origin master [����, Զ��master��Ϊ��, ����-u����,git��ѱ���master���͵�origin/master��,������]
# 5. git push origin master [֮��, ���������͵�Զ�� �Ϳ��Բ���-u����]

# ��Զ�̿��¡ [���㿪��, �ȴ���Զ�̿�,Ȼ���Զ�̿��¡]
# 1. ��github�ϴ���repository
# 2. git clone git@github.com:blingyuan/learngit.git [��¡��һ�����ؿ�]

# github ֧�ֶ���Э��, git://ʹ�� ssh , Ҳ֧��httpsЭ��
# httpsЭ���ٶ���,ÿ�����ͻ������������,��ĳЩ��˾ֻ����http�˿�,��ֻ��ʹ��https



# git ��֧
# һ. ����/�ϲ���֧
# ����dev��֧, �л���dev��֧
git checkout -b dev
# �鿴��ǰ��֧
git branch [*��ʾ��ǰhead��λ��]
# �ڵ�ǰ��֧�����޸�,Ȼ����ӵ��ݴ���,�ύ,�л�������֧,�ϲ�,�ύ��Զ�̷�֧,ɾ����֧
git add readme.txt;
git commit -m "";
git checkout master; 
git merge dev;  [����mergeʱ, master��֧û���޸�, ����"���ٺϲ�/fast forward"]
git push origin master;
git branch -d dev

# ��.�����ͻ[����mergeʱ, master��֧�н��й��޸�, �޷�����"���ٺϲ�"]
# �鿴��ͻ�ļ�
1.git status
2.�򿪳�ͻ�ļ�,�����ͻ,����add��commit
3.git log --graph --pretty=oneline --abbrev-commit[�鿴��֧�ϲ����]

# ��. ��֧�������
# fast forwordģʽ��, ɾ����֧��,�ᶪʧ��֧��Ϣ
# ���Ҫǿ�ƽ��� fast forwardģʽ,git����mergeʱ��������һ���µ�commit,�Ϳ��Կ�����֧��Ϣ
1. git checkout -b dev
2. git add readme.txt
3. git commit -m ""
4. git checkout master
5. git merge --no-ff -m "" dev [ʹ��--no-ff����fast forwardģʽ,��ʱmergeʱҪ�� -m ����, ��Ϊ�Ǵ���һ���µ�commit]

# ��ʵ�ʿ�����,Ӧ����ѭ�ļ�������ԭ��
# 1. master��֧Ӧ���Ƿǳ��ȶ���,�����������°汾,ƽʱ����������ɻ�
# 2. ÿ�������Լ�dev��֧

# ��. Bug��֧[�޸�bug]
# �龰: ����bug[����001]����,��ʱ����dev��֧��readme.txt[֮ǰ��git add/git commit��]�ļ���û�޸���,���ܽ���commit,�и��½����ļ� test.txt[û�б�git add/git commit��],����master��֧�и�����bug��Ҫ����,Ҫ�л���֧
# ��ȷ����:[�����ֳ�]
1. git add test.txt[�½����ļ�ʱδ��׷�ٵ��ļ�, ��Ҫ������git׷��]
2. git status [on branch dev, new file: test.txt, modified: readme.txt]
3. git stash [�����ֳ�,saved working directory]
# �л�����Ҫ�޸�bug�ķ�֧,������Ӧ��bug��֧,�޸�,add, commit, merge,delete
1. git checkout master[��master��֧���޸�bug]
2. git checkout -b issue-001[����bug��֧, �޸�readme.txt�ļ�]
3. git add readme.txt
4. git commit -m "fix bug 001" readme.txt
5. git checkout master
6. git merge --no-ff -m "merge bug 001" issue-001
# bug�޸���, �л���dev��֧, ��������,�ָ�
1. git checkout dev
2. git stash list
# �ָ�����
1. git stash apply[�ָ���,�����ݲ�ɾ��] + git stash drop[ɾ��stash]
2. git stash pop[�ָ���ͬʱɾ��stash����]

# С��: �޸�bugʱ,��ͨ�������µ�bug��֧�����޸�,Ȼ��ϲ�,���ɾ��
#		����ͷ����û�����ʱ, �Ƚ������ֳ�git stashһ��,Ȼ��ȥ�޸�bug,�޸�����git stash pop,�ص������ֳ�

# ��. Feature��֧[����¹���]
# �龰: ����¹���ʱ,����һЩʵ�����ʵĴ���. һ��ÿ���һ���¹���,����һ��feature��֧,����,��ɺ�,�ϲ�,ɾ��feature��֧
# �������ڽӵ�һ��������,����"feature-001"
1. git checkout -b feature-001
2. git add feature-001.txt
3. git commit -m "add feature-001"
# �������, �л���dev��֧, ׼���ϲ�
4. git checkout dev
# ��ʱ, �ϼ�����,�¹���ȡ��,��֧����
5. git branch -d feature-001 [error: the branch is not fully merged, ��ʱ��֧��û�ϲ�,���ɾ��,���ᶪʧ]
6. git branch -D feature-001 [ʹ�ô�д��-D����,ǿ��ɾ��]
# С��: ����һ���µ�feature,����½�һ����֧
#		�������һ����δ�ϲ��ķ�֧,����ʹ�� git branch -D <name>ǿ��ɾ��

# ��. ����Э��
git remote [�鿴Զ�̿����Ϣ]
git remote -v [�鿴����ϸ����Ϣ fetch/push��ַ]
# ���ͷ�֧
1. git push origin master [�����ص�master��֧���͵�Զ�̵�origin��֧��]
# Ҫ����������֧,��dev
2. git push origin dev
# ��Щ��֧��Ҫ����
#1.	master��֧������֧,Ҫʱ����Զ��ͬ��
#2. dev�ǿ�����֧,�Ŷӳ�Ա�������湤��,Ҳ��Ҫ��Զ��ͬ��
#3.	bug��֧�����ڱ����޸�bug,û��Ҫ���͵�Զ��
#4. feature��֧�Ƿ�����,ȡ�����Ƿ�������С���һ�𿪷�

# ץȡ��֧
# �龰: һ��С���Ҫ���뿪��,Ҫ��clone��Ŀ, Ҫ��dev��֧�Ͻ��п���,���봴��Զ��origin��dev��֧������,��dev�Ͻ����޸�,ʱ��ʱpush��Զ��[Զ����dev��֧]
1. git clone git@github.com:blingyuan/learngit.git
2. git checkout -b dev origin/dev [���ش���dev��֧,����Զ�̵�dev��֧����]
3. git add env.txt
4. git commit -m "add env"
5. git push origin dev
# С�����origin/dev��֧�����������ύ,��һλС���Ҳ�޸����ļ�,����ͼ����
6. git push origin dev [error: failed to push, git pull before pushing again]
# ����ʧ��, �� git pull�����µ��ύ��origin/devץȡ����,�ڱ��غϲ�,�����ͻ,������
7. git pull[��� git pullҲʧ��,��û�б��ص�dev��֧��Զ��origin/dev������,��������]
8. git branch --set-upstream-to=origin/dev dev
9. git pull [����pull]

# ����Э���Ĺ���ģʽ��һ���ǣ�
1. ��ͼ�� git push origin <branch-name>�����Լ����޸ĵ�Զ��
2.�������ʧ�ܣ�����ΪԶ�̷�֧�ȱ��ص��£���Ҫ��git pull��ͼ�ϲ�
3.��κϲ��г�ͻ��������ͻ�����ڱ����ύ
4.���û�г�ͻ���߽����ͻ������ git push origin <branch-name>��������
 ��� git pullʱ��ʾno tracking information����˵�����ط�֧��Զ�̷�֧֮������ӹ�ϵû�н�����������
 git branch --set-upstream-to <branch-name> origin/<branch-name>

# С��:
#	1. �鿴Զ�̿���Ϣ, git remote -v
#	2. �����½��ķ�֧��������͵�Զ��, ���������ǲ��ɼ���
#	3. �ӱ������ͷ�֧, ���git push origin branch-name, �������ʧ��,����git pullץȡԶ���µ��ύ
#	4. �ڱ��ش�����Զ�̷�֧��Ӧ�ķ�֧,ʹ��git checkout -b branch-name origin/branch-name, ���غ�Զ�̷�֧���������һ��
#	5. �������ط�֧��Զ�̷�֧�Ĺ���,ʹ��git branch --set-upstream branch-name origin/branch-name
#	6. ��Զ��ץȡ��֧,ʹ�� git pull,����г�ͻ,Ҫ�ȴ����ͻ

# ��ǩ����
#  һ�㷢��һ���汾��ͨ���ڰ汾���д�һ����ǩ��tag������������Ψһȷ���˴��ǩʱ�̵İ汾���������Ը��ݱ�ǩȡ����Ӧʱ�̵���ʷ�汾��
#  ���ԣ���ǩҲ�ǰ汾��һ������
# ���ʣ� Ϊʲô��commit����Ҫ����tag
# ��Ϊcommit_id��һ��hashֵ�������ң�tag��һ���������˼�ס������������֣����Ǹ�ĳ��commit����һ���
git tag <name>
git tag v1.0 [���ǩ������Ĭ���Ǵ��������ύ��commit_id�ϵ�]
git tag [�鿴���б�ǩ����ǩ����ʱ��˳���г������ǰ���ĸ����]
# ������ ���Ǵ��ǩ�ˣ������µ�commit�ˣ���ô����ǰ��commit_id���ǩ
# ������ �ҵ���ʷ�ύ��commit_id�����ϾͿ���
git log --pretty=oneline --abbrev-commit [�鿴�ύ��־]
git tag <tag_name> <commit_id> [��ĳ��commit_id��tag]
# ��������˵���ı�ǩ��-aָ����ǩ���� -mָ��˵������
git tag -a <tagname> -m "version 0.1 released" commit_id
git show <tagname> [�鿴˵������]
git tag -d <tagname> [ɾ����ǩ]
# �����ı�ǩ��ֻ�洢�ڱ��أ������Զ����͵�Զ��
git push origin <tagname> [����ǩ���͵�Զ��]
git push origin --tags [һ��������ȫ��δ���͵�Զ�̵ı��ر�ǩ]
# ���Ҫɾ��Զ�̵ı�ǩ
1. �ȴӱ���ɾ��
git tag -d <tagname>
2. ��Զ��ɾ��[push]
git push origin :refs/tags/<tagname>
