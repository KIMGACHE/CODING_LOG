# AWS
배포 AWS 로그인-대시보드-오른쪽 상단에 계정명 왼쪽에 있는 나라(리전)을 서울로 설정해줘야함-왼쪽상단에 검색부분에 EC2검색-인스턴스시작-OS를 Linux로 할듯?Amazon Linux(Redhat기반)-내리다보면 인스턴스 유형에서 프리 티어 사용 가능 인것을 확인(1년정도는 무료)-키 페어에서 새 키 페어 생성(필수) 이름은 임의로 설정,RSA,.pem으로 설정하고 키페어를 생성한다-그럼 자동으로 키페어가 다운로드되는데 잃어버리면 안된다.- 스토리지 구성에서 보조기억장치를 프리티어의 최대GB까지 올려준다.30GB-인스턴스 시작-모든 인스턴스 보기

인스턴스의 상세정보를 보면 퍼블릭IPv4주소가 있는데 이는 계속 바뀌기 때문에 주의 인스턴스를 우클릭하면 탭이 여러개 뜸 - 인스턴스 중지가 종료이다. 좌측 탭에 네트워크 및 보안 - 탄련적 IP - 탄력적 IP주소 할당 - 할당 (이거를 할당받는거 자체가 돈이나가기때문에 EC2만 삭제하는게 아니라 얘도 같이 삭제해야한다 연결하지않았더라도 할당만해도 요금이 청구된다.) 할당된 ip를 체크하고 우클릭 - 탄력적IP주소 연결 - 인스턴스 선택을 클릭하면 실행중인 인스턴스가 보임 선택 - 연결 다시 대시보드를 가보면 퍼블릭IPv4주소가 탄력적 IP주소로 변경된 것을 볼 수 있다.

퍼블릭 IPv4주소를 복사 - putty에 Host Name에 붙여넣기 - 좌측 SSH탭 Auth - Credential - preivate key file을 넣어줘야한다. puttygen을 킴 - 상단의 conversions - import key에 아까 다운받았던 키페어를 넣어준다. save private key를 누름 - .ppk확장자로 변경되는 것을 볼 수 있다. - ppk파일을 아까 private key file에 넣어주고 session탭에가서 Open한다. 로그인 id는 ec2-user를 치면 private key가 비밀번호가 되어 자동으로 로그인된다

EC2의 대시보드 - 클릭 후 하단의 보안 탭 - 인바운드 규칙(외부에서 내부로 들어올 때 규칙), 아웃바운드 규칙(내부에서 외부로 나갈 때 규칙) - 보안그룹 클릭 - 인바운드 규칙 편집 - 0.0.0.0/0으로 설정되어있을것 -> 모든 곳에서 접근가능 - 이를 내IP선택 - 규칙추가 - 사용자 지정TCP - 포트설정(ex 8080) anywhere Ipv4를 누르고 0.0.0.0/0인 상태로 규칙저장

putty 환경에서 df -h 입력 - Mounted on에 /경로에 Size가 현재 사용할 수 있는 보조기억장치의 크기를 볼 수 있다. free -h라고 입력하면 주기억장치의 크기를 볼 수 잇음(너무적어서 보조기억장치를 주기억장치로 끌어온다-swap)

TimeZONE설정 date를 입력하면 대한민국 시간과 맞지않는 것을 볼 수 있다. sudo rm /etc/localtime sudo ln -s /usr/share/zoneinfo/Asia/Seoul /etc/localtime 입력 후 다시 date를 입력하면 한국 시간과 맞게된다.

swap 설정 sudo dd if=/dev/zero of=/swapfile bs=128M count=16 128메가를 16개사용 128x16 => 약 2기가

스왑 파일에 대한 읽기 쓰기 권한 업데이트 sudo chmod 600 /swapfile

Linux 스왑 영역 설정 sudo mkswap /swapfile

스왑공간에 스왑파일을 추가하여 스왑파일을 즉시 사용할 수 있도록 변경 sudo swapon /swapfile

절차가 정상적으로 변경되었는지 확인 sudo swapon -s

free -h를 써보면 Swap에 2Gi 추가된다.

이 모든 과정이 컴퓨터가 재부팅되면 모두 사라지므로 재부팅되어도 자동 설정되게끔하는 파일을 추가 sudo vi /etc/fstab 커서를 가장 아래로 내리고 o를 눌러 insert모드 진입 이후 /swapfile swap swap defaults 0 0 입력후 esc로 insert모드 탈출한 후 :wq를 입력하여 저장후 종료

mount -a 입력

JDK 설치 sudo su sudo yum install -y java-21 java --version으로 버전 확인가능

cf. 여러 jdk 중 선택(안해도됨) alternatives --config java

GIT 설치 sudo yum install -y git

MySQL설치 mysql community download를 웹에서 검색 mysql yum repository로 들어가기 가장위에거를 download들어감 - no thanks어쩌구를 우클릭하여 링크 주소 복사를 선택 putty에서 sudo yum install -y https://dev.mysql.com/get/mysql84-community-release-el9-1.noarch.rpm(아까 복사한 주소)

MySQL서버 설치 sudo yum install -y mysql-server

sudo systemctl status mysqld -> 가서보면 inactive sudo systemctl start mysqld sudo systemctl status mysqld -> active

sudo systemctl enable mysqld

초기 패스워드 확인 (중요) sudo vi /var/log/mysqld.log 로그들 중에 temporary password에서 끝에보면 비밀번호가있음 그걸 복사함 - 상단의 putty탭을 우클릭하여 duplicate session을 통해 새로운 putty창을 열고 mysql -u root -p 입력후 비밀번호 입력하는 칸에 방금 복사한 비밀번호를 사용함 sql창에서 alter user root@localhost identified by 'Zhfldk11!'; 입력 (대문자필요)

현재까지 putty에서 mysql에는 접속되지만 local에서 workbench로 접근은 불가함.

create user dbconn@'%' identified by 'Zhfldk11!'; 입력 -> dbconn이라는 user를 만듬 이때 dbconn은 모든 ip주소에서 사용가능 grant all privileges on . to dbconn; -> 모든 DB에 대한 권한 획득 quit해서 sql을 나가준뒤 local에서 workbench를 실행한다.

MySQL Connections에서 +를 눌러 새 Connection을 만든다. hostname은 AWS의 public IPv4를 복사하여 입력한다. username도 dbconn으로 설정 port는 3306이나 AWS에서 설정해주지 않았으므로 AWS 실행중인 인스턴스의 보안탭으로 감 - 보안그룹에 있는 링크 클릭 인바운드 규칙 편집 DB의 경우 아무나 접근하면 안되므로 내IP에 Port를 3306으로 설정한다. 비밀번호는 위에서 설정한 Zhfldk11!로 가능하다
