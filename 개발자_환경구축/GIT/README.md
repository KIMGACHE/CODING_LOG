# GIT

분산형 버전 관리 시스템의 한 종류. <br>

## 기본 명령어

**git init** : 해당 경로에 .git이라는 숨김폴더가 생성된다. <br>
**git status** : 해당 경로에 변경사항이 출력된다. <br>
**git add [파일명]** : staging area에 파일을 추가한다. <br>
```
git add a.txt
```
**git commit** : staging area에 추가한 파일을 local repository에 업로드한다. (-m 옵션을 통해 메시지를 남길 수 있다.) <br>
처음 git을 사용할 때에는 사용자가 누군지 알 수 없기때문에 깃헙 이메일과 깃헙에서 사용하는 이름을 입력해주어야 한다. <br>

git config --global user.email "gache5764@naver.com" <br>
git config --global user.name "KIMGACHE” <br>

```
git commit -m "V0.0 a.txt added"
```

**git reset** : commit을 취소하는 명령어 <br>
3종류의 reset 옵션이 있다. <br>
1. --soft : 파일과 staging area에 내용이 모두 그대로 남아 있다.
2. --mixed : 파일은 남아있으나 staging area에는 내용이 사라진다.
3. --hard : 파일과 staging area가 모두 사라진다.
<br>

```
git reset --hard [로그ID]
git reset --mixed [로그ID]
git reset --soft [로그ID]
```
그럼 reset을 하면 되돌릴 수 없나? <br>
git reflog를 하면 commit시점별로 로그가 남아있고 로그ID를 통해 원하는 시점으로 reset하면된다.










