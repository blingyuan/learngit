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
# 1. github�����SSH
# 2. ����repository
# 3. git remote add origin git@github.com:blingyuan/learngit.git [����һ��Զ�̿�] 
# 4. git push -u origin master [����, Զ��master��Ϊ��, ����-u����,git��ѱ���master���͵�origin/master��,������]
# 5. git push origin master [֮��, ���������͵�Զ�� �Ϳ��Բ���-u����]