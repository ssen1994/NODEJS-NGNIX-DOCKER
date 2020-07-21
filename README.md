DOCKER
======

1. Dockerfile 만들기(첫자는 무조건 대문자)
2. Dockerfile을 통한 docker image 빌드하기
    - docker build --tag [옵션] [Dockerfile이 위치하는 위치]
    - dockerfile과 서버 파일의 위치가 같으면 위치를 .로 쓴다. 
   예) docker build --tag node_server:0.0.1 .
3. 빌드 결과 생성된 이미지 확인 
    - docker images
4. 생성된 이미지로 컨테이너 만들기  
    - docker create --name [서버명] -p [외부 포트:컨테이너 내부포트] [이미지명:버전태그]
    예)docker create --name NODE_SERVER_0 -p 3000:3000 node_server:0.0.1
5. 컨테이너 확인하기
    - docker ps -a
6. 컨테이너 실행하기
    - docker start [서버명]
    예) docker start NODE_SERVER_0

* 버전 태그 업그레이드 해서 파일 변경하고 다시 확인하는 과정(기존 파일은 제거) <br>
docker build --tag node_server:0.0.2 [Dockerfile위치] <br>
docker images <br>
docker rm -f NODE_SERVER_0 <br>
docker ps -a <br>

* Docker로 여러 개의 서버 띄우기(컨테이너 생성) <br>
docker create --name NODE_SERVER_1 -p 3001:3000 node_server:0.0.1 <br>
docker create --name NODE_SERVER_2 -p 3002:3000 node_server:0.0.1 <br>
docker create --name NODE_SERVER_3 -p 3003:3000 node_server:0.0.1 <br>

* Docker로 여러 개의 서버 실행 <br>
docker start NODE_SERVER_1 <br>
docker start NODE_SERVER_2 <br>
docker start NODE_SERVER_3

<br>
<br>

NGNIX
===== 

1. 설치
    - 윈도우는 별도 설치
    - 맥은 Brew install nginx
2. 서버 조작 방법
    - 시작 : nginx
    - 중지 : nginx -s stop
    - 재시작 : nginx -r reload
3. 로드 밸런싱 설정 
    - (1) /usr/local/nginx/conf, 
      (2) /etc/nginx, 
      (3) /usr/local/etc/nginx

      중 ngnix.conf 를 찾아 설정 (맥은 3번)
