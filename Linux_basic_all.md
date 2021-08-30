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

- 파일시스템

  - 운영체제 안에 있음
  - file들이 잘 관리되고 동작할 수 있도록하는 시스템

- 계층구조

  - Tree형태의 계층구조이다
  - Linux의 모든 dir은 root아래에 존재한다
  - ![tree](https://user-images.githubusercontent.com/73927750/131306463-6422366d-96f1-462b-bad4-d6faa170620f.JPG)

- 리눅스 vs 윈도우

  - 만약에 윈도우에 새로운 drive처럼 HDD등을 추가한다면?

    -> 윈도우에서는 각각의 drive가 독립적으로 존재가능

  - 하지만 리눅스에서는 모든 dir이 root의 아래에 존재해야함

    -> 개별적으로 관리되는 것이 아닌 newdir을 생성하고 root의 하위에서 관리한다(==mount)

- 파일의 종류

  1. 일반파일 : 말 그대로 일반 파일
  2. 디렉토리 : == 폴더
  3. 심볼릭 링크 파일 : == 바로가기
  4. 블록 디바이스 파일 : 사용자가 os를 거쳐 블록 디바이스를 직접 제어하기 위한 파일
  5. 문자 디바이스 파일 : 사용자가 os를 거쳐 문자 디바이스를 직접 제어하기 위한 파일
  6. 파이프 파일 : 프로세스간 통신에 사용되는 파이프 파일
  7. 소켓 : 프로세스간 통신에 사용되는 소켓 파일

- 디렉토리

  1. / : root(최상위)
  2. /bin : 모든 사용자가 사용할 수 있는 여러가지 실행 파일들이 위치
  3. /sbin : 관리자 권한으로 실행하는 실행 파일들이 위치(sudo)
  4. /etc : 설정 파일(주의)
  5. /lib : 라이브러리
  6. /home : 사용자의 홈 디렉토리 -> 멀티유저들을 위해 존재, 각 계정끼리 서로 접근 X
  7. /mnt : CD나 USB등 mount할 때 사용하는 디렉토리
  8. /proc, /sys : 시스템 정보를 설정/조회하는 디렉토리
  9. /tmp : 임시
  10. /usr : 사용자가 추가한 실행, 라이브러리 파일을 저장하는 디렉토리
  11. /dev : 디바이스 드라이버가 사용하는 디바이스 파일 디렉토리

- 아이노드(inode)

  - 파일의 구조 중 하나
  - file의 여러가지 data를 저장해놓은 구조체
  - name - idnoe - data 로 구성되어 있음 -> 하나의 file
  - ![inode](https://user-images.githubusercontent.com/73927750/131309343-7650747b-e9bb-4684-8e83-bfec0f0d6dc0.JPG)

- 하드링크(hard-link) vs 소프트링크(soft-link, symbolic-link, symlink)

- 하드링크 : inode를 공유하기 때문에 사실상 누가 원본인지 알 수 없음, 파일이름만 다르고 나머지는 전부 같음

  - ls -i == 아이노드 확인법

  - ln `<파일명>` `<새로운 파일명>` == 하드링크 만드는 법

  - stat `<파일명>` == 파일에 대한 자세한 정보를 볼 수 있음

  - ln apple hello -> apple라는 파일의 inode를 공유하는 hello라는 파일을 생성한다

    -> 이 둘은 서로 연결되어 있기 때문에 2개 중 1개를 수정해도 모두 수정된다.

- 소프트링크 : 바로가기와 비슷, 원본 file의 경로를 가지고 있음

  - ln -s `<파일명>` `<새로운 파일명>` : 소프트링크 만드는 법

    -> ln -s pineapple hello

    -> 이 둘은 서로 연결되어 있기 때문에 2개 중 1개를 수정해도 모두 수정된다.

- 차이점?

  - 하드링크는 inode노드 주소를 공유한다

  - 하드링크는 파일을 다른 디렉토리로 이동해도 연결상태를 유지 O

  - 소프트링크는 바로가기처럼 그냥 단순한 연결관계

  - 소프트링크는 파일이 다른 경로로 이동하면 연결관계가 유지 X

    -> 하지만 절대경로를 이용해서 만들면 디렉토리가 변경되어도 유지 O

    -> ln -s pineapple /home/user/tmp == /tmp에 pineapple가 생성된다

    -> 이는 pineapple의 원본의 위치과 복사된 pineapple의 위치가 다르지만 절대경로로 생성하였기 때문에 연결 관계가 유지 O

- ![link](https://user-images.githubusercontent.com/73927750/131317857-45b84c24-2c10-4d2e-a190-388ff47cf35d.jpg)



## 5. 사용자와 그룹

- 사용자

  - 사용자는 사람이 아니라 하나의 계정을 의미함

  - 하나의 linux에서는 여러 계정이 독립적으로 사용될 수 있다.

  - 사용자, 그룹, root로 나눠진다.

  - cat /etc/passwd == 시스템에 어떤 계정이 존재하는지?

  - cat /etc/group == 시스템에 어떤 그룹이 존재하는지?

  - sudo adduser user2 == user2 계정생성

    -> /home/user2 생성

  - su(switch user) -user2 == user2 계정으로 로그인

    -> exit == 로그아웃 -> 원래있던 user1으로 돌아옴

  - sudo deluser user2 --remove -home == /home아래에 있는 user2에 관한 모든 파일, 계정을 삭제

  - sudo addgroup animals == animals 그룹을 생성

  - sudo adduser dog --ingroup animals == user dog를 animals 그룹안에서 생성

- 파일 소유권(ownership)

  - ls -l == 현재 디렉토리의 목록을 자세하게 확인할 수 있다.
  - ![파일소유권](https://user-images.githubusercontent.com/73927750/131319367-cd0d4563-dab3-4f9b-bc69-59eceaefe966.jpg)

- 파일 접근 권한(permission)

  - 말 그대로 파일에 접근할 수 있는 권한

  - r : read(읽기), w: write(수정), x : execute(실행)

  - 8진 표기법과 의미 표기법이 있다

  - ![파일권한](https://user-images.githubusercontent.com/73927750/131319675-37cb531b-ca12-4d98-ac20-c943d69940e9.jpg)

  - 8진 표기법

    - 2진법 3자리로 이루어진 것을 8진법으로는 1자리로 표시가능
    - chmod 664 testfile == testfile에 -rw-rw-r의 권한을 부여
    - chmod 764 testfile == testfile에 -rwxrw-r--의 권한을 부여
    - ![8진표기법](https://user-images.githubusercontent.com/73927750/131320066-4a7c4121-2f05-472b-a6b6-044b2e8ed8a7.JPG)

  - 의미표기법

    - 알맞은 의미를 선택해서 부여함
    - chmod g+rw testfile == testfile에 -rwxrw-r--중 group에 rw권한을 추가
    - ![chmod](https://user-images.githubusercontent.com/73927750/131320252-96afe85c-3bdd-4b39-8d25-8d62df7dd54f.jpg)

  - script 파일

    - 순차적으로 실행해야하는 명령들을 저장해 놓은 group
    - #!/bin/bash == bash script생성(nano로 작성, vim도 같음) -> 반드시 써줘야함(이것이 script파일이다!! 라고 알리는 행위임)
    - script파일 만들어서 실행하는 방법
      1. nano testscript로 #!/bin/bash를 통해 script파일 생성
      2. testscript -> 실행 X -> 이유는? -> 환경변수에 등록되어 있지 않음...
         1. PATH에 넣기(환경변수)
         2. 절대경로 : /home/user2/testscript
         3. 상대경로 : ./testscript
      3. 환경변수 등록 후 다시실행 -> 실행 X -> 실행권한이 없기 때문 -> -rw-r--r-- -> 권한을 부여해 줘야함
         1. chmod 744 testscript -> 권한이 부여되었고  user2가 실행 가능
         2. 실행 O
         3. ./testscript == testscript를 실행하는 명령어 -> success

    

## 6. 프로세스와 시그널

- 프로세스 : 실행중인 program

- 사전적 의미 : 진행중, 실행중인 program

- 프로그램 vs 프로세스

  - 프로그램 : 디스크에 저장되어 있는 실행파일, 정적
  - 프로세스 : 프로그램을 실행하면 생성됨(메모리에), 여러개 만들수 있음, 메모리상에서 독립적임, 동적
  - ![program_and_process](https://user-images.githubusercontent.com/73927750/131322505-28abf7cf-54cc-4e40-9fff-7d86bf61ae4d.jpg)

- 프로세스 스케줄링

  - 여러 프로그램의 동시 실행 : 멀티스레드와 비슷함
  - CPU가 여러개의 process들을 빠르게 순차적으로 수행 -> CPU가 많아지면 능률이 올라감.

- 프로세스 상태

  - CPU가 process를 처리할 때 process의 상태
  - waiting : 대기중
  - running : 진행중
  - blocked : process가 외부자원과 작업하면서 소요되는 시간을 기다리는 상태(동기)
  - ![process_state](https://user-images.githubusercontent.com/73927750/131323049-403af0aa-b32a-4584-9c85-271456e9c089.JPG)

- 프로세스 계층구조

  - PID(process Id) : 프로세스가 가지는 고유한 id값
  - 부모프로세스와 자식프로세스
    - 프로세스는 부모와 자식과의 관계를 가진다.
    - 부모프로세스는 자식프로세스가 종료되면 뒤처리를 한다.
  - init프로세스
    - booting ->init 프로세스생성(pid1, 모든프로세스의 부모프로세스임) -> 다른 프로세스로 뻗어나감(계층구조로...)
  - 프로세스 종료처리
    - 부모프로세스는 자식프로세스가 종료되면 뒤처리(메모리 등)를 한다.
  - 고아프로세스와 좀비프로세스
    - 고아프로세스 : 부모프로세스가 자식프로세스보다 먼저 종료됨 -> 나중에 자식프로세스의 뒤처리를 할 부모가 없어짐 -> init프로세스가 해당 자식을 입양함
    - 좀비프로세스 :  자식프로세스가 먼저 종료 -> 자식이 종료되었다는 signal -> 원래는 부모프로세스가 자식프로세스의 뒤처리를 해야하지만 바빠서 못함 -> 자식프로세스는 정상적으로 뒤처리가 되지 못함(반만 종료됨) -> 좀비프로세스(자원낭비)

- 프로세스 종료 상태

  - 프로세스가 종료될 때 넘겨주는 정보

  - 부모프로세스에게 남은 정보를 넘김

  - 일반적으로 linux에서는 0 == 성공

  - 직전 command의 exit status는?

    -> echo $ -> 0이 나오면 정상적으로 실행종료됨

  - signal

    - 프로세스를 강제종료하기 위한 command

      - kill -l == kill 옵션을 볼 수 있음
      - kill -9 `<PID>` == 해당 프로세스 강제종료(가급적이면 kill -TERM `<PID>`먼저...)

      

- 표준 스트림 : 모든 프로세스는 3가지 스트림을 갖는다

  - 표준 입력
  - 표준 출력
  - 표준 에러
  - ![stream](https://user-images.githubusercontent.com/73927750/131354359-65023353-a4b8-4957-b9bc-99c2a31d5ec0.JPG)

- 파일 디스크립터

  - 파일을 대변하는 객체
  - 파일에 대한 작업을 하기 위해서는 파일 디스크립터를 열어야함
  - 프로세스로 열린 파일 디스크립터 목록을 관리
  - ![file_descriptor](https://user-images.githubusercontent.com/73927750/131354767-fc9cd8b0-32b3-4cbc-ba34-67a45f0389e6.jpg)

- 포어그라운드 프로세스와 백그라운드 프로세스

  - 가장 큰 차이점 : 사용자와의 입력 연결 여부

  - 포어그라운드 프로세스

    - 쉘의 표준 입력이 연결된 프로세스
    - 쉘의 표준 입력이 연결된 프로세스
    - 사용자의 입력값이 주어질때까지 기다림 

  - 백그라운드 프로세스

    - 쉘의 표준 입력이 연결되지 않은 프로세스
    - 쉘의 표준 입력이 연결된 프로세스
    - 사용자의 입력은 필요하지 않고 알아서 돌리고 싶을 때 사용

  - background 실행방법

    -> ./process.sh & == 실행

    -> fg를 입력 == foreground로 전환됨 -> ctrl + c 가능

  - foreground 실행방법

    -> ./process.sh == 실행

    -> ctrl + z == 잠시 멈춤

    -> bg를 입력 == background로 전환됨

  - jobs == 현재 background로 실행되고 있는 프로세스를 확인시켜줌

    -> ex) [1] ~, [2] ~ ...

    -> %`<숫자>` fg == `<숫자>`에 해당되는 프로세스가 foreground로 전환됨

- 데몬프로세스

  - 보이지 않는 곳에서 스스로 일하고 있음
  - 백그라운드 프로세스로 동작하기 위해 만들어진 프로세스
  - 표준 스트림을 모두 갖고 시작하지만 모두 닫아버림 -> 쉘과의 입출력 교환 불가
  - 부모 프로세스를 init프로세스로 변경

- 시그널(signal)

  - 비동기(asynchronous) 이벤트를 처리하기 위한 프로세스간 통신(inter process communication)
  - 동기 vs 비동기
  - 동기 : 다른 작업이 끝날 때까지 기다림
  - 비동기 : 기다리지 않고 알아서 자신의 작업을 수행함
  - ![signal](https://user-images.githubusercontent.com/73927750/131359491-511592fe-94d1-4d7e-9a7e-01c992b76a29.jpg)
  - 주요 시그널
    1. SIGCHLD - 자식프로세스 종료 - 무시
    2. SIGINT - 사용자가 인터럽트 생성(ctrl + c) - 종료
    3. SIGKILL - 종료 명령 - 종료
    4. SIGTERM - 조건에 따른 종료 - 종료



## 7. 리디렉션과 파이프라인

- 출력 리디렉션 : >

  - [n] > [filename]

    -> ls > abc == abc라는 파일안에 ls의 출력물을 저장한다

  - 대상 파일이 존재하는 경우 덮어쓴다

  - noclobber설정 시 덮어쓰기 시도 시 에러 발생

- 추가 모드 출력 리디렉션 : >>

  - [n] >> [filename]

    -> ls >> abc == abc파일에 덮어 쓰는 것이 아니라 뒤에 추가된다(append)

  - 스트림을 대상 파일 끝에 추가 후 저장

- 파일 디스크립터로 리디렉션 : >&

  - [n] >& [FD]
  - `>`와 동일하지만 대상 파일 대신 대상 파일 디스크립터로 지정
  - 표준 출력관 표준 에러를 한꺼번에 출력하고 싶을 때 자주 사용

- 표준 출력 및 표준 에러 동시 리디렉션 : &>

  - & > word

    -> ls &> result == ls에서 오류가 발생하더라도 표준출력처럼  result에 저장된다.

  - 파일 디스크립터로 리디렉션보다 편리하게 사용가능

- 입력 리디렉션 : <

  - [n] < [filename]

    -> wc(word count) < process.sh == wc에게 사용자가  < 후에 입력한 것처럼 내용을 전달한다

- Here documents : <<

  - [command] << [-]DELIM
  - ... == < 처럼 file이 아닌 사용자가 직접 ... 영역안에 내용을 입력
  - DELIM
  - 프로그램 표준 입력으로 multi-line string 전달
  - 코드블록의 내용이 임시 파일로 저장됐다가 프로그램의 표준 입력으로 리디렉션
  - DELIM은 다른 단어로 변경가능(EOF, END)

- Here strings : <<<

  - [command] <<< word

  - Here documents의 한 줄 버전

    -> cat > hellotext <<< "Hello World" == "Hello World"가 cat으로 전달되어 출력되고 hellotext에 저장된다

- 파이프라인(pipeline)

  - 프로그램 간 상호작용

  - program -> stdout -> 연결 -> stdin -> program

  - ![pipeline](https://user-images.githubusercontent.com/73927750/131362702-fabb5958-8c84-472d-bc0d-dcd8d164afe4.jpg)

  - 파이프라인 : |

  - command1 [| command2] ... == command1의 표준출력이 command2의 표준입력으로 연결됨 + 추가적으로 더 연결해서 사용가능

    -> cat process.sh | wc == process.sh의 출력결과가 wc의 입력으로 넘어옴

  - command1 [|& command2] ... == command1의 표준출력과 표준에러가 command2의 표준입력으로 연결됨

  - 전체 파이프라인의 exit status는 마지막 실행 커맨드의 exit status임

  - pipefail 옵션이 설정되어 있다면 실패한 커맨드가 존재하면 실패로 처리됨 

<출처> 내용정리와 사진은 ProgCoach4U님의 강의를 듣고 정리한 내용입니다.
