# MySQL Study

* 그동안 공부를 게을리 한 탓인지...SQL에 대한 기본적인 지식들을 까먹은것 같다. SQL은 정말 중요하다. 그래서 SQL 기초부터 다시 공부하려고 한다.

* 데이터베이스 생성
  ```
  DROP DATABASE IF EXISTS test; #이미 test라는 DB가 있으면 삭제
  CREATE DATABASE test; # test DB 생성
  USE test; # test DB 사용
  ```

*  테이블 만들기
  ```
  예시:)

  CREATE TABLE students (
     ID INT(11) NOT NULL AUTO_INCREMENT,
     Name CHAR(35) NOT NULL DEFAULT '',
     Age int(11) NOT NULL DEFAULT 25,
     MajorCode VARCHAR(10),
    PRIMARY KEY (ID)
    ) DEFAULT CHARSER=utf8;
  ```

  * Student라는 테이블을 만든다. ID는 정수형으로 NULL 값을 허용하지 않고 `AUTO_INCREMENT`설정을 해서 자동으로 증가하도록 설정하였다.

  * Name은 문자열 35자로 설정했고, NULL 값을 허용하지 않는다. 그리고 Default값은 ''이다.

  * Age는 정수형이고 NULL 값을 허용하지 않으며 Default값은 25이다.

  * MajorCode는 문자열 10자로 설정했다.

  * Primary key는 unique한 값을 의미하며 학생별로 ID는 유일한 값을 가지기 떄문에 Primary key를 ID로 설정

  * Default charset=utf8로 설정


# CRUD(Create, Read, Update, Delete)

|이름|SQL|
|:--:|:--:|
|Create(생성)|INSERT|
|Read(읽기)|SELECT|
|Update(갱신)|UPDATE|
|Delete(삭제)|DELETE|

* Read에 해당하는 SELECT

  * 데이터 읽기
    ```
    select * from [table];

    select * from students;
    # students 테이블로부터 모든 학생 정보를 가져오기

    select * from students where Age = 25;
    # students 테이블로부터 나이가 25세인 학생 정보를 가져오기
    ```

* Create에 해당하는 INSERT

  * 데이터 삽입
    ```
    insert into [table] values(value1, value2 ...)

    insert into students values(9, "호날두", 35, "CHE");

    insert into students(Name, Age, MajorCode) values("호날두", 35, "CHE");
    # ID필드가 AUTO_INCREMENT이므로 ID를 적어주지 않고 삽입 가능
    ```

* Update에 해당하는 Update

  * 데이터 변경
    ```
    update [table] set column1 = value1, column 2 = value2 ... where some_column = some_value;

    update students set Name = "메시", where Name = '';
    # 조건에 부합하는 row 업데이트
    ```

* Delete에 해당하는 Delete

  * 데이터 제거
    ```
    delete from [table] where [condition];
    
    # 조건에 해당하는 row 삭제
    # 만약 조건을 달지않고 delete from [table];을 하면 전체 테이블이 삭제되므로 delete를 할 때는 이점을 유의해야 함.
    
    delete from students where name = "홍길동";
    # students 테이블에서 이름이 홍길동인 학생 row 정보 삭제
    ```
