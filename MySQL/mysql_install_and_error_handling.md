# Mysql 설치 및 에러 해결 (window10 기준)

- 먼저 window에서 mysql을 설치해주기 위해 mysql community server를 설치
  - [mysql community server 5.7.17 Download](https://downloads.mysql.com/archives/community/) 최신버전이 아닌 5.7.17버전 설치
   (5.7.18 버전부터 my-default.ini 파일을 제공하지 않는다고 한다.)


- 설치를 하고 C:\ 에 압축을 푼다음 환경변수를 설정해준다.
  - 시스템 변수 path에 C:\mysql-5.7.17-winx64\bin 추가


- 그리고 my-default.ini 파일을 수정하여 my.ini 파일 만들기(처음 상태는 이렇다.)
  ```
  #basedir = .....
  #datadir = .....
  #port = .....
  # server_id = .....```

- 이것을 수정해줘야 한다.(주석(#) 지우기)
  ```
  basedir = C:\mysql-5.7.17-winx64
  datadir = C:\mysql-5.7.17-winx64\data (data가 저장될 경로)
  port = 3306
  # server_id = .....```


- 설정 파일(my.ini) 초기화 해주기.
<pre>C:\mysql-5.7.17\bin>mysqld --initialize</pre>

- Window에 MySQL 서비스 등록하기.
  - cmd를 관리자 권한으로 실행 -> mysql 설치된 폴더로 접속 -> bin 폴더
  - mysqld --install
    => "Service successfully installed"가 출력되면 성공
  - mysqld --remove : 서비스 지울 때

-  Mysql 서비스를 시작.(cmd 관리자 권한으로 실행)
<pre>net start mysql</pre>
- 서비스 중지를 하기 위해서는
<pre>net stop mysql</pre>

- 그러나 mysql 서버에 접속 하려고 했을 때 에러가 났다.
<pre>"Can't connect to MySQL server on 'localhost' (10061)"</pre>

- 명령프롬프트(관리자)에서 mysqld --console --explicit_defaults_for_timestamp --skip-grant-tables 를 치면 방화벽 메시지가 뜬다.

  - 방화벽 해제 메시지가 뜨면 허용을 하고(화면 끄지 않기) 다시 명령프롬프트를 띄우고 나서 <pre>mysql -u root mysql</pre>를 치면 문제없이 mysql 서버에 접속 할 수 있다.


- 하지만 mysqld --console --explicit_defaults_for_timestamp 를 치지 않고 mysql 서버에 접속하려고 하면 위의 에러가 뜬다.

    - 그래서 3306포트를 열어주기 위해 <strong>window 방화벽에서 3306 포트</strong>를 열어준다.


  - Window10 제어판 -> window 방화벽 -> 인바운드 규칙 -> 새 규칙
    -> 3306 포트 열어주기

- 포트를 열어주고 나서 명령프롬프트 창에서 mysql -u root mysql을 치고 접속을 시도하면 mysql 서버에 성공적으로 접속 성공!

- 추가적으로 python3에서 Mysql을 사용하기 위해서는 mysqlclient 패키지를 설치 해야 한다.
<pre>pip install mysqlclient</pre>
