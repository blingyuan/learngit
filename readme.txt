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

# ��. Bug��֧
# �龰: ����bug[����001]����,��ʱ����dev��֧��readme.txt[֮ǰ��git add/git commit��]�ļ���û�޸���,���ܽ���commit,�и��½����ļ� test.txt[û�б�git add/git commit��],����master��֧�и�����bug��Ҫ����,Ҫ�л���֧
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

