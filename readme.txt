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

# HEADָ��ǰ�汾, ^, ~<num>
# ���� �汾����, �ص���ȥ
git reset --hard commit_id
# �鿴�ύ��ʷ
git log
# �鿴������ʷ, ȷ��Ҫ�ƶ����İ汾,�ص�δ��
git reflog
