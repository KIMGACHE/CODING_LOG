# 미들웨어

**미들웨어란?** <br>
운영체제와 상관없이 Application을 사용할 수 있도록 환경을 조성해주는 프로그램.<br>
하나의 시스템에서 다양한 목적의 소프트웨어가 동시에 수행되거나, 복수의 시스템의 소프트웨어가 서로 연계되어 수행되는 경우에도 안정적으로 실행될 수 있도록 OS와 소프트웨어 사이에서 다양한 기능을 지원하는 소프트웨어이다.<br>

<br>

**주요기능** <br>
1. **분산시스템 SW**
   - 물리적으로 흩어져 있는 다수의 컴퓨팅 환경에서 사용자가 하나의 시스템처럼 사용할 수 있도록 구성된 소프트웨어
   - ex) 웹 애플리케이션 서버, 연계 통합 솔루션, 실시간 데이터 처리, 분산 병렬 처리, TP모니터
3. **IT 자원관리**
   - IT자원에 대한 관리 정책을 기반으로 지속적으로 모니터링하고 성능과 가용성을 관리하는 기능을 제공하는 소프트웨어
   - ex) 시스템 관리, SW 실행관리, 네트워크 관리, IT 서비스 운영관리    
5. **서비스 플랫폼**
   - 서로 다른 서비스들을 하나의 통합 환경에서 인터랙티브하게 사용할 수 있도록 해주는 인터넷 기반 환경구성 기술
   - ex) IoT플랫폼, 클라우드 서비스 플랫폼, UI/UX 프레임워크, CDN
7. **네트워크 보안**
   - 네트워크에 연결된 호스트들의 송수신 정보 탈취 및 변조를 통한 불법적인 서비스 이용을 방지하는 기술
   - ex) 네트워크 접근 제어, 보안 통신, 침입방지/사고대응, 보안 관리

# 개발환경 구축
1. Openjdk 11.0.2 download
   환경변수 설정 - 시스템 변수 - Path - jdk bin폴더경로를 Path에 새롭게 추가
3. Tomcat 9.0 download
5. Eclipse download
   
Eclipse 설정
1. window - preferences - general - workspace - text file encoding에 other UFT-8인지 체크
2. window - preferences - files라고 입력 - CSS Files에 Encoding부분을 UTF-8로 적용 (HTML, JSP Files도 마찬가지로 적용)
3. File - New - Other - server 입력 후 더블클릭 - Apache - Tomcat 9 버전 - Tomcat 경로 입력(폴더 내부로 한번은 들어가보기)
4. File - New Dynamic Web Project 선택 - Target Runtime(미들웨어 선택) - Tomcat 9 선택
5. 프로젝트 우클릭 - Properties - Java Build Path - Server Runtime이 Tomcat 9 버전인지 확인
6. 프로젝트 우클릭 - Properties - Project Facets - Java버전을 현재 Eclipse버전과 같게 설정
7. 프로젝트 우클릭 - Properties - Server - Tomcat 9 버전 선택 후 Apply
8. src - main - webapp - WEB-INF - lib에 Tomcat 9 버전 lib폴더에 들어있는 jsp-api.jar과 servlet-api.jar을 복사하여 넣는다.

<br>

# GIT과 Eclipse 연동하기
프로젝트 우클릭 후 - Team - Share Project - Use or create repository in parent folder or project 체크
   
