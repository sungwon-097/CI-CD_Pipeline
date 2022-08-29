-   section01

### Development Process

-   Waterfall
    -   프로젝트의 각 단계별 구분이 뚜렷, 순차적인 프로젝트 관리 방법론
    -   각 과정은 이전단계가 완료 된 후에만 진행됨
        1. 요구사항정의
        2. 분석/설계
        3. 구현
        4. 테스트
        5. 운영
    -   이전단계로 돌아가기가 어렵기 때문에 고객의 니즈를 바로 반영하기가 어려움
-   Agile
    -   Waterfall 방식이 지나치게 과정에 의존적이기 때문에 효율성이 떨어질 수 있는 문제점을 최소화하려 함
    -   반복적인 과정을 통해 더 나은 방법으로 보완함

### Cloud Native Architecture

-   클라우드 인프라 환경에서 운용되기 위한 어플리케이션 또는 서비스를 최적의 상태로 유지하고 사용 할 수 있도록 해 주는 Architecture
    ![img](/Section01/img_src/CNA.png)

### Cloud Native Application

1. 마이크로서비스로 개발
2. 마이크로서비스를 클라우드 환경에 배포하고 사용하기 위한 컨테이너 가상화 기술
3. 서비스에 문제가 생겼을 때 바로바로 수정하고 반영하기 위한 DevOps
4. CI/CD 자동화 Pipeline에 의해 자동으로 통합되고 빌드, 테스트, 배포과정을 통해 운용함

### Cloud Native - DevOps

-   엔지니어가 프로그래밍, 빌드하고 직접 시스템에 배포하여 서비스를 개선해 나가는 일련의 과정, 또는 문화

### Cloud Native - CI/CD

-   개발자 및 팀에 의하여 개발된 결과물에 대해 지속적인 통합과 배포를 하는 프로세스
-   CI(Continuous Integration) : 작업된 코드에 컴파일, 테스트, 패키징 작업(Build, Test, Merge 자동화로 인해 코드의 품질이 올라감)
-   CD : 지속적인 배포와 제공
    -   Continuous Delivery : CI에서 통합된 데이터를 검증하고 최종 배포를 수동으로
    -   Continuous Deployment : 자동으로 전 과정을 배포

> 수많은 서버를 수동으로 관리하다보면 개발 이외의 시간에 할애를 많이 하게 되어 비효율적(CI/CD는 MSA 개발에 중요한 구성 요소)

### CI/CD Flow

1. Git push
2. Jenkins : CI/CD 자동화  
    2-1. Maven or Gradle : Build tools  
   // CI
3. Docker : Container Runtime
4. kubernetes : Docker container의 배포 관리(컴퓨터 시스템과 애플리케이션, 서비스의 자동화된 설정, 관리, 조정하는 Ochestration 도구)
5. AWS, NCP  
   // CD

![img](/Section01/img_src/CICD.png)

### Jenkins

-   지속적인 통합과 배포 -> Work Flow를 제어(CI/CD)
-   다양한 Plugins 연동이 가능하다
    -   Maven, Gradle
    -   VCM or SCM(git, bitbucket)
    -   Java, Python, Nodejs

![img](/Section01/img_src/JENKINS.png)

: Development -> User Acceptance Testing -> Production
