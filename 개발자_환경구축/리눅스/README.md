# 리눅스
<br>
**LINUX OS의 특징**<br>
1. 무료
2. 오픈소스 (내가 원하는 형태의 리눅스를 만들 수 있다.)
3. 플랫폼에 독립적으로 사용 가능하다.

## 기본 명령어
---
~ : Home Directory를 의미<br>
sudo su : 관리자 계정으로 전환<br>

passwd [변경할 비밀번호] : 접속중인 사용자의 비밀번호를 변경<br>
passwd [계정명] [변경할 비밀번호] : 해당 계정의 비밀번호를 변경<br>
<br>
reboot / shut down -r now / init 6 : 재부팅<br>
power off / shut down -h now / halt / init 0 : 부팅<br>
<br>
ifconfig : 네트워크 확인 명령어<br>
pwd : print working directory, 현재 위치 확인 명령어
<br>
<br>
**cd** [이동경로] 현재 디렉토리(working directory) 변경 명령어<br>
**경로 표현방식**<br>
1. 절대경로 : 모든 경로를 다 적는 방식. ex) /home/test/abc
2. 상대경로 : 현재 디렉토리를 기준으로 경로를 표현하는 방식. ex) 위의 예시에서 home으로 이동할때  cd ../..
   
<br>

**ls** : 파일, 디렉토리 목록을 출력하는 명령어<br>
-a : 모두보기<br>
-l : 자세히보기<br>
-R : 하위 항목까지 보기(하위 폴더)<br>
-d : 해당 디렉토리의 상세정보 보기<br>
<br>

**mkdir** [경로/폴더명] : 폴더 생성 (한번에 여러개도 생성할 수 있다)
-p : 경로상에 존재하지않는 폴더로 생성한다.
```
mkdir /test/abc/gache (이때 root디렉토리에 test abc gache폴더는 존재하지않지만 모두 생성해줌)
```
<br>
**touch** [경로/파일명] : 파일 생성
-d : 파일의 생성 일자를 바꿀 수 있다.
-t : 파일의 생성 년월일을 바꿀 수 있다.


























