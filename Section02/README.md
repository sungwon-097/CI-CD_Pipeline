-   section02

### Git

-   Manage Jenkins / Jenkins plugin / avaliable / github
-   Manage Jenkins / Jenkins plugin / Global Tool Configuration / git

### Maven

-   Manage Jenkins / Jenkins plugin / avaliable / Maven Integration
-   Manage Jenkins / Jenkins plugin / Global Tool / add Maven

### Tomcat

-   Manage Jenkins / Jenkins plugin / avaliable / deploy to container

-   실습 3) 주의점
    -   Tomcat은 Local, Jenkins는 Docker Container 환경에서 실행중
    -   $ ifconfig > en0 > inet: 의 ip주소를 Tomcat URL에 입력 해 주어야 Docker 환경에서 기동 중인 Jenkins에서 경로를 찾을 수 있다

### Setup PollSCM

-   Project / Configure / Build Triggers / check PollSCM
-   주기적으로 update 된 내용을 확인하여 Build 자동화
-   schedule에 얼마 주기로 확인 할지 입력
-   변경내용이 생긴 후 schedule이 되면 Build

### SSH + Docker

1. war 파일을 SSH를 이용해서 복사
2. Dockerfile + \*.war -> Docker image build
3. Docker image -> 컨테이너 생성

-   Manage Jenkins / Jenkins plugin / avaliable / publish over SSH
-   Manage Jenkins / System Settings / Publish over SSH
