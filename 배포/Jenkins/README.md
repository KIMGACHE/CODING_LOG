# JENKINS
코끼리 - Tasks - build - bootJar 더블클릭

프로젝트에 build - lib - 파일 우클릭 - OpenIn - Explorer
열린 폴더에서 cmd실행
java -jar demo-0.0.1-SNAPSHOT.jar 입력
그리고 localhost로 가서 해당 프로젝트 url을 입력하면 실행됨

플젝에서 build폴더 삭제
해당 프로젝트가 있는 경로에서 cmd창 열기
(gradlew가 build파일을 만드는데 사용되는 커맨드?이다)
cmd에서 gradlew build 입력(build폴더가 생성됨)
cmd에서 build -> libs 경로에있는파일을 실행 (아래커맨드)
java -jar demo-0.0.1-SNAPSHOT.jar
해당 파일이 배포할 파일이다?

깃헙에서 repository하나 생성
방금 프로젝트 폴더내에서 cmd를열어 repository와 연결해준다
(깃헙페이지에 나와있는 커맨드 그대로사용하는거추천)

ec2-user(putty)에서 cd ~
mkdir test
cd test
git clone REPOSITORY주소
프로젝트를 받아오면 해당 폴더로 들어가
gradlew build라고 친다(에러남) - 실행권한이 없음
chmod a+x gradlew
./gradlew build

error때문에 원 프로젝트에 settings.gradle로 가서
plugins {
    id 'org.gradle.toolchains.foojay-resolver-convention' version '0.8.0'
}
를 (상단에) 입력하고 push한다.
그리고 putty에서 pull하여 ./gradlew clean build를 실행하면 해결됨

build - libs 경로에서 java -jar demo-0.0.1-SNAPSHOT.jar을 입력
ec2에서도 SpringBoot를 실행가능하다

웹에서 ec2의 퍼블릭주소:포트를 쓰거나
DNS:포트를 입력하면 페이지로 띄워진다.
--------------------------------------------------------여기까지가 수동배포

jenkins download 검색
Red Hat계열 클릭

putty에서 jenkins repository를 다운받고 jenkins를 다운한다.
(jdk는 다운받을 필요없음)
jenkins의 기본 설정포트가 8080이고 현재 프로젝트도 8080을 사용하고 있으므로
포트를 바꿔주어야한다.
vi /usr/lib/systemd/system/jenkins.service
:se nu로 라인수를 볼 수 있다
:70 하면 70번라인이 나옴 거기에 있는
Environment="JENKINS_PORT=8080"을 수정한다
i를 눌러 9090으로 변경 esc로 command mode로 변경
:wq로 탈출

ec2 instanceid - 보안 - 보안그룹 - 인바운드 규칙 편집
규칙추가 사용자 지정 TCP 9090 내 IP(배포서버기 때문에 아무나접속해서는 안된다?)

sudo su
systemctl restart jenkins
systemctl enable jenkins	(재접속시에도 사용할수있도록?먼말모르겠음)

내IP:9090으로 접속하면 jenkins화면이 뜸(url이 있음)
그럼 비밀번호를 입력하라고 하는데 putty에서 
cat [url]을 입력하면 비밀번호를 준다 그걸 입력

그럼 기본설정으로 할것이냐 커스텀하게 설치할것이냐를 물어본다
설치하고나면 관리자 계정을 만들고 jenkins서버 주소설정을 하고나면
jenkins dashboard가 나온다

좌측 하단에 Built-in Node를 클릭
(error /tmp 의 사이즈가 너무 작아서 문제가있다)

putty에서 umount /tmp -> 실행중이라 안된다고나옴
vi /etc/profile
shift+g를 누르면 가장 아래로 내려감 -> o를 누르면됨

sudo umount /tmp
sudo mount -t tmfs -o size=5g,mode=1777 tmpfs /tmp
라고 입력 (5기가 권한부여)

jenkins dashboard에 가보면 오류가 사라져있다

또 다른 해결방법(이걸 쓸거면 위에 profile에 적은 내용은 지워야함)
sudo su
vi /etc/fstab
tmpfs   /tmp    tmpfs   size=5g,mode=1777   0   0
:wq

젠킨스 - jenkins관리 - system - GitHub - add github server

Name 입력

Add클릭 - jenkins - Kind를 Secret text로 설정

배포할 예정인 github사이트로 이동 - settings - developer settings
- personal access tokens - token(classic)

workflow와 write:packages빼고 모두 체크표시 - update token
Jenkins로 돌아가서 Secret에 token을 넣어준다 - add

Credential(비밀번호)를 Token으로 사용한다
test connection해서 4999나오면된다. 그러면 저장

-----------------
다시 Jenkin 관리  - Tools - JDK installations에 jdk경로를 넣어줘야한다.
putty에서 alternatives --config java로 경로를 찾을 수 있는데
이때 bin폴더 전까지만 복사한다.
Gradle installtion로가면된다.
intellij - gradle - gradle-wrapper.properties를 보면 qjwjsdmf dkf tn dlTek.

다시나와서 plugin탭에서 Available plugin탭가면




/var/lib/jenkins/workspace/WEB_DEPLOY_TEST/build/libs

java -jar demo.0.0.1-SNAPSHOT.jar
