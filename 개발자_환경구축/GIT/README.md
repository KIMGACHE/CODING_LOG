# GIT

분산형 버전 관리 시스템의 한 종류. <br>

## 기본 명령어

**git init** : 해당 경로에 .git이라는 숨김폴더가 생성된다. <br>
**git status** : 해당 경로에 변경사항이 출력된다. <br>
**git add [파일명]** : staging area에 파일을 추가한다. <br>
```
git add a.txt
```
<br>

**git commit** : staging area에 추가한 파일을 local repository에 업로드한다. (-m 옵션을 통해 메시지를 남길 수 있다.) <br>
처음 git을 사용할 때에는 사용자가 누군지 알 수 없기때문에 깃헙 이메일과 깃헙에서 사용하는 이름을 입력해주어야 한다. <br>

git config --global user.email "gache5764@naver.com" <br>
git config --global user.name "KIMGACHE” <br>

```
git commit -m "V0.0 a.txt added"
```
<br>

**git log** : 로그를 출력한다. (--oneline 옵션을 통해 간략한 버전으로 볼 수 있다.)

<br>

**git reset** : commit을 취소하는 명령어 <br>
3종류의 reset 옵션이 있다. <br>
1. --soft : 파일과 reset하는 시점에 staging area에 존재하는 내용이 모두 그대로 남아 있다.
2. --mixed : 파일은 남아있으나 reset하는 시점에 staging area에 존재하는 내용이 사라진다.
3. --hard : 파일과 staging area가 모두 사라진다.
<br>

```
git reset --hard [로그ID]
git reset --mixed [로그ID]
git reset --soft [로그ID]
```
<br>
그럼 reset을 하면 되돌릴 수 없나? <br>
git reflog를 하면 commit시점별로 로그가 남아있고 로그ID를 통해 원하는 시점으로 reset하면된다.
<br>

## Branch

branch를 만들어야 하는 이유
1. Version 관리가 용이하다.
2. 분업하기에 용이하다.
3. 하나의 branch에서 test 작업을 하기에 힘듦.
<br>

**Brnach 명령어** <br>
git branch : branch 목록을 출력한다.
git branch [branch명] : 해당 이름의 branch를 생성한다. (-M 옵션을 주면 가장 상위의 branch 이름을 설정) <br>
git switch [branch명] : 해당 이름의 branch로 변경한다. <br>
(git log를 통해 현재 사용중인 branch가 무엇인지 확인 할 수 있다.) <br>

새롭게 branch를 생성하고 해당 branch로 바꿔 새로운 commit을 발생시키면 master에서는 dev에서 일어난 일을 알지 못하므로 <br>
master에는 해당 파일이 존재하지 않는다.<br>

<br>

git merge [병합할 branch명] : branch를 병합한다.
1. fast-forward : 병합을 할 때 최근 commit 위치로 병합한다.
2. non-fast-forward : 병합을 할 때 옵션을 넣어 commit 위치를 지정하여 병합한다.

<br>

동일한 파일의 내용이 서로 다르다면 충돌이 일어난다. <br>
충돌을 해결하고 나서 병합을 진행하려면 --continue 옵션을 merge에 준다. <br>
충돌을 무시하고 병합을 진행하려면 --abort옵션을 merge에 준다. <br>

## GIT
Local Repository에서 작업한 내용을 원격 Repository로 PUSH하는 방법 <br>
1. git init
2. git branch -M main
3. 작업한 뒤 commit
4. git remote add origin(이름바꿀수있음) [GITHUB REPOSITORY주소]
5. git push origin
6. 가장 처음 push를 진행했다면 git push --set-upstream origin main 입력 후 5번 진행
