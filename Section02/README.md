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
-   Manage Jenkins / System Settings / Publish over SSH / hostname : en0의 IP 주소

### 실습 4-1

```cmd
(local)$ docker run --privileged --name deploy-server -itd -p 10022:22 -p 8081:8080 -e container=docker -v 
/sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host edowon0623/docker-server:m1 /usr/sbin/init
// --privileged 로 root 권한 획득, 10022:22 -> container 내부의 ssh 서버는 22번 local환경에선 충돌을 막기 위해 10022를 
사용해 접속함(portforwarding)

(local)$ ssh root@localhost -p 10022
// ssh 접속 후 암호 입력

(root)$ systemctl start docker
// docker 활성화

(root)$ systemctl status docker
// active(running 확인)

(root)$ vi Dockerfile
// tomcat:9.0사용, deploy할 hello-world.war 파일로 변경

(root)$ docker run -p 8080:8080 --name mytomcat docker-server:latest
// 8080 -> ssh, 8080 -> tomcat

// http://localhost:8081/hello-world/ 로 접속해 연결 확인
```

### 실습 4-2

```cmd
$ docker build --tag=cicd-project -f Dockerfile .;
$ docker run -d -p 8080:8080 --name mytomcat cicd-project:latest
// 위의 상태에서 생성된 docker image와 .war 파일을 제거 후 ssh 설정에서 exec command에 위의 명령어를 입력
```

---

-   docker image를 삭제하지 않고 4-2의 build를 jenkins로 실행하게 되면 docker run 명령이 충돌, 별도의 제어가 필요함(Section3에서)
