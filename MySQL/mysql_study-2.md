# MySQL Study

* Order by

  * 특정 필드를 기준으로 정렬 가능
  * 기본적으로 오름차순(ASC)으로 설정.
  * 내림차순 : DESC

  ```
  select *
      from students
      order by Age DESC;
      
  # students 테이블의 모든 정보를 Age 필드 기준으로 내림차순으로 정렬하기
  ```


* Aggregation
  * count, sum, avg 등 각 필드별로 aggregation 가능
  * https://dev.mysql.com/doc/refman/5.7/en/group-by-functions.html
  (다양한 Aggregate Function 참고)

  ```
  select sum(Age)
      from students;
  # students 테이블에서 Age 필드 summation 하기
  ```


* group by
  * 특정 필드를 기준으로 grouping

```
select *
    from students
    group by MajorCode;

# MajorCode 필드를 기준으로 grouping 하여 students 테이블에서 데이터 읽어오기

select *
    from students
    group by MajorCode
    having Age > 25;

# MajorCode 필드를 기준으로 grouping 하여 Age가 25 초과인 students 테이블의 데이터 읽어오기    
```
