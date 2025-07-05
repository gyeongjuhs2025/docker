# docker
20250705, docker

# 도커 강의 교안

## YAML 이란?

서로 다른 시스템 간 데이터 연동과 호환성을 위해 다양한 포맷(CSV, XML, JSON, Properties 등)이 사용됩니다.  
최근에는 가독성이 좋고 주석을 달 수 있는 YAML이 널리 사용됩니다.  
YAML은 "YAML Ain't Markup Language"의 약자로, 데이터 중심 설계를 강조합니다.

### YAML 특징

- **Key: Value** 형태로 작성
- 들여쓰기로 계층 구조를 표현 (파이썬과 유사)
- 주석 사용 가능 (`#`)
- 배열 표현: `-` 기호 사용
- 여러 문서를 한 파일에 작성 가능 (`---`)

### 사용 예시

```yaml
student:
  name: 둘리
  age: 10
  major: 컴퓨터공학

members:
  - 둘리
  - 또치
  - 도우너

## 주요 사용처
* Docker Compose
* Kubernetes
* Spring Boot 설정 파일
* CI/CD 툴 (GitHub Actions, GitLab CI 등)

# 도커(Docker)란?
* 컨테이너 기반 오픈소스 가상화 플랫폼 (2013년 최초 공개)
* 소프트웨어를 컨테이너라는 표준 단위로 패키징
* 애플리케이션 실행에 필요한 모든 요소 포함 (라이브러리, 코드 등)

## 도커의 장점
* 환경에 독립적인 실행
* 배포, 확장 용이
* 동일한 개발 환경 제공
* 빠르고 가벼운 서버 운영

## 가상 머신과 비교
| 구분     | 가상 머신 (VM)  | 도커 (Container)  |
| ------ | ----------- | --------------- |
| OS 독립성 | 별도 OS 필요    | 호스트 OS 공유       |
| 실행 속도  | 느림          | 빠름              |
| 자원 사용량 | 많음          | 적음              |
| 용도     | 다양한 OS 필요 시 | 경량화, 빠른 배포 필요 시 |

# 도커 이미지와 컨테이너
* 이미지: 실행 가능한 애플리케이션 상태를 저장한 압축 파일
* 컨테이너: 이미지를 실행한 인스턴스 (실제 동작 단위)

# Docker Desktop 설치
[이미지 저장소] (https://hub.docker.com)
* Mac, Linux, Windows 지원
* GUI 환경 제공
* WSL2 또는 Hyper-V를 활용해 Linux 커널 접근

# 컨테이너 생성 및 실행
[설치 가이드: Get Docker](https://docs.docker.com/get-started/get-docker/)
## 컨테이너 내부 접속
```
docker run -d -p 8072:80 --name myhttpd2 httpd
```
* docker ps: 실행 중인 컨테이너 확인
* docker cp index.html myhttpd2:/usr/local/apache2/htdocs: 파일 복사
```
docker exec -it myhttpd2 bash
```
## Docker Volume
* 컨테이너 데이터 영속성 보장
* 명령어 예시:
```
docker volume create vtest

docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=1234 -v vtest:/var/lib/mysql --name mysql_db -e TZ=Asia/Seoul mysql
```
## 네트워크와 포트 포워딩
* 호스트와 컨테이너 간 통신 위해 포트 매핑 필요
```
-p 호스트포트:컨테이너포트
예) -p 8080:80

여러 웹 서버 컨테이너 동시 운영 가능
```
## 주요 명령어 요약
* 컨테이너 목록 확인: docker ps
* 이미지 목록 확인: docker images
* 컨테이너 정지 및 삭제: docker stop, docker rm
* 이미지 삭제: docker image rm

## 도커 활용 사례
* 여러 서버의 동일 환경 배포
* 새로운 버전 라이브러리 테스트
* 서비스 확장 및 자동화

## 참고 자료
[Docker 공식 문서] (https://docs.docker.com/)
[레드햇 도커 소개] (https://www.redhat.com/ko/topics/containers/what-is-docker)
