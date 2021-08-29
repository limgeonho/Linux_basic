## 1. 리눅스란 무엇인가?

- ubuntu, centos, fedora
- 리눅스는 운영체제이고 다양한 배포판들이 있기 때문에 자신에게 적절한 배포판을 이용하면 된다 

## 2. 운영체제(OS)

- 하드웨어와 소프트웨어 자원을 관리하는 시스템 소프트웨어
- ![os](https://user-images.githubusercontent.com/73927750/131223438-b3075aea-95a2-4577-bf02-d40140e71ad4.JPG)
- 운영 체제 주요 구성요소

  1. 커널(kernel) - 하드웨어와 app을 관리하고 대부분의 역할을 담당
  2. 프로그램 실행과 멀티 테스킹 - 동시에 여러가지 일을 수행
  3. 인터럽트 - 하드웨어 -> OS
  4. 메모리 관리 - HDD -> MEM -> CPU
  5. 파일 시스템 - OS와 HDD, SSD 사이에서 파일단위를 어디에 저장할지, 불러올지 관리하는 매개자
  6. 디바이스 드라이버 - 디바이스를 잘 동작시키기 위한 시스템 소프트웨어
  7. 네트워킹 - TCP / IP
  8. 사용자 인터페이스
- 패키지 관리 시스템
  - 사용자가 원하는 프로그램을 패키지 관리 시스템에 요청하면 패키지 관리 시스템 -> repository에서 데이터를 가져와서 전달해줌

- 라이브러리 동적 로딩과 의존성
  - ![library](https://user-images.githubusercontent.com/73927750/131223740-160772b6-594c-462a-8e48-b7e531cc0a85.JPG)
- 가상화
  - 하나의 하드웨어에서 하나의 OS만 사용하는 것이 아니라 가상머신을 통해 여러개의 OS와 시스템을 사용할 수 있음
  - ![vm](https://user-images.githubusercontent.com/73927750/131223806-47367313-530b-4be6-b9fb-9022d76db97c.JPG)
  - VMWare player, Virtualbox사용
  - 따라서, 윈도우를 사용할 경우 가상머신을 만들고 가상머신 위에 리눅스OS를 설치하여 사용한다.
  - 윈도우와 리눅스를 하나의 컴퓨터안에서 독립적으로 사용가능하다.

## 

## 3. 기본 쉘 명령어

- 리눅스 쉘 == H/W -> kernel -> shell(가장 겉에 있음, 껍질)

- 사용자가 터미널을 통해 shell(bash)을 사용함 -> 리눅스 프로그램을 사용

- bash(born again shell) -> CLI(command line interface)로 명령

- 명령어

  1. 메뉴얼 조회 : man

     - man ls == ls에 관한 설명 -> /`<찾고 싶은 내용>` 

  2. 파일 목록 / 내용 조회 관련 명령어 : ls, cat, head, tail

     - ls == 파일 목록을 보여줌
     - cat == 텍스트 전체
     - head == 텍스트 윗부분
     - tail == 텍스트 아래부분

  3. 검색 / 탐색 관련 명령어 : grep, find

     - grep == 찾고 싶은 내용을 찾아줌 -> grep "찾고 싶은 내용" `<파일명>`

     - find == 지정한 디렉토리에서 모든 파일을 찾아온다 

       -> find -name "*.conf" -print == 현재 dir에서 .conf로 끝나는 모든 파일의 name을 print

       -> find | grep conf == 현재 dir파일전체를 검색 후 grep로 넘겨서 conf가 들어간 것을 전부 찾기

     - 상대경로 vs 절대 경로

       - 상대경로 : 현재위치를 기준으로 원하는 경로를 찾아가는 것
       - 절대경로 : root(/)부터 쭉 내려오면서 원하는 경로를 찾아가는 것

  4. 압축 / 해제 관련 명령어 : tar, gzip/gunzip, zip/unzip

     - gzip == .gz파일로 압축

     - gunzip == .gz파일을 원래대로 돌림(압축풀기)

       -> find > filelist == find 한 것들을 filelist에 넣기

       -> gzip filelist == filelist.gz 생성(압축)

       -> file filelist.gz == filelist.gz에 관한 정보

       -> gunzip filelist.gz == filelist로 돌아옴(압축해제)

       -> 참고로, 리눅스에는 확장자가 없음

     - tar

       -> tar를 이용해서 하나로 합치는 것(압축X)

       -> tar.gz == tar로 합치고 gzip으로 압축한 것임

       -> tar -czf `<생성할 파일명>``<압축할 파일들>`

       -> tar -czf test.tar.gz filelist.gz 사진 == filelist와 사진이 압축된 test.tar.gz이 생성됨(압축)

       -> tar -zxf test.tar.gz == 현재 위치한 디렉토리에 (압축해제)

  5. 시간 관련 명령어 : date, cal

     - date == 내가 설정한 지역의 시간이 나옴(KST)

     - date -u == UTC기준 시간이 나옴

     - date +%Y-%m-%d == 2021-08-24처럼 formatting이 가능

     - cal == 달력그림이 나옴

       -> cal 2021 == 2021년 달력이 나옴

  6. 기타 명령어 : pwd, history, exit, echo, which

     - pwd == 현재 디렉토리 주소 검색

     - history == 지금까지 사용한 command목록 -> !`<숫자>` == `<숫자>`번째 command 실행

     - exit == shell 빠져나오기

     - echo == 출력

       -> echo aaa == aaa출력

       -> echo $PWD == 현재 dir을 출력

       -> echo $PATH == 현재 환경변수를 출력

     - which ls == ls가 어디에 있는지?

  7. 관리자 권한 실행 : sudo

  8. 패키지 매니저 : apt

     - user -> apt -> repository

     - apt를 통해 원격에 있는 repository에 접근하여 원하는 것을 설치, 삭제, 조회

       -> sudo apt install `<패키지명>` == `<패키지명>` 설치

       -> sudo apt remove `<패키지명>` == `<패키지명>` 삭제

       -> apt list == repo전체 목록

       -> apt list --installed == 내 pc에 있는 패키지 목록들

  9. 텍스트에디터 : nano, vim

     - windows의 메모장과 비슷함
     - ^ == ctrl키
     - M == alt키

  10. 기타명령어

      - rm -rf `<name>` ==  `<name>` 에 해당하는 것을 전부삭제(위험)

      - rmdir testdir == testdir을 삭제(만약, testdir이 비어있지 않은 경우에는 삭제 불가 -> rm -rf이용)

      - mv testdir testdir2 == testdir2로 이름이 변경됨

      - mv testdir2 /tmp == /tmp 아래로 testdir2를 이동

        -> ls /tmp == /tmp 아래에 testdir2가 있는지 확인

        -> mv /tmp/testdir2 . == 원래 존재하던 현재 디렉토리로 이동(복귀)



## 4. 파일

