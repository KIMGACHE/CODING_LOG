## Oracle

**계정 생성** <br>
create user '계정이름' identified by '비밀번호';<br>

**권한 부여** <br>
grant connect, dba to '계정이름'; <br>

**여러 문법들**
1. 와일드카드
   - %: 문자수 제한 없이 모든 문자
   - _: 문자수 제한이 있는 모든 문자
   ```
   select * from userTbl where userId like '김%'; -- userId가 김으로 시작하고 뒤에 무슨 문자가 몇개가 오던 상관없다.
   select * from userTbl where userId like '_병_';
   -- userId가 '병' 앞에 어떤 문자던 한 문자, 뒤에 어떤 문자던 한 문자가 오는 것을 조회한다. 
   ```
3. 여러개의 값들 중 하나를 선택해야 할 때
   - any : 여러개의 값들 중 모든 것을 포함하는 경우, or연산과 비슷하다.
   - all : 여러개의 값들 중 모든 것에 충족되는 경우, and연산과 비슷하다.
   ```
   select * from userTbl where height > any (select * from userTbl where age =25);
   -- 이때 나이가 25인 사람의 키가 [177,158,172]라면 세가지 키를 모두 포함할 수 있는 height > 158이 where절이 된다.
   select * from userTbl where height > all (select * from userTbl where age =25);
   -- 이때 나이가 25인 사람의 키가 [177,158,172]라면 세가지 키가 모두 충족되는 height > 177이 where절이 된다.
   ```
5. 정렬 order by
   ```
   select name , mDate from usertbl order by mDate;
   -- order by 기준으로 정렬한다. 기본값은 오름차순이고 desc를 뒤에 붙여 내림차순으로 정렬도 가능하다.(사전편찬순)
   ```
7. distinct
   - select에 조회될 항목을 넣기전에 distinct를 넣으면 조회되는 항목들 중 중복된 항목은 포함하지 않는다.
9. group by
   ```
   select addr from userTbl group by addr; -- addr을 기준으로 묶어서 조회할 수 있다.
   select height from userTbl group by height having height >= 170;
   -- group by를 사용한 쿼리에는 where문을 사용할 수 없어 having문을 통해 조건을 걸어줄 수 있다.
   ```
10. 집계함수
    - sum,avg,min,max,count등등 여러 집계 함수가 있다.
    ```
    select prodname, sum(price*amount) from buyTbl group by prodname;
    -- 상품명과 해당 상품의 가격*구매수를 곱한 값을 출력한다. 이때 상품명으로 묶어 출력한다.
    ```
12. having
    ```
    select prodname, sum(price*amount) from buyTbl group by prodname having sum(price*amount) >=200;
    ```
14. rollup
15. 제약조건 설정하기
    ```
    alter table TEST_01 add constraint PK_USERID primary key(userid);
    -- TEST_01테이블에 PK_USERID라는 이름의 기본키를 userid라는 컬럼에 추가하겠다.

    alter table TEST_01 add constraint FK_01 foreign key(prod_id) references Prod_tbl(prod_id);
    -- TEST_01테이블에 FK_01이라는 이름의 외래키를 만든다. 이때 TEST_01의 prod_id가 Prod_tbl테이블의 prod_id를 참조한다.

    -- UNIQUE 제약조건 : 중복은 허용하지않으나 null은 허용한다.

    create table TEST_09
      (
	   userid char(8) primary key,
	   name varchar(10),
       birthyear int check (birthYear >= 1900 and birthYear <=2023),
       mobile1 char(3) null,
       constraint CK_name CHECK (name is NOT NULL)
      );
    -- check 제약조건 : 테이블에 값을 넣을 때 해당 조건을 만족해야 값을 삽입할 수 있다.
    
    ALTER TABLE TEST_09 MODIFY (mobile1 DEFAULT '010');
    -- Default : 제약조건은 아니고, 값을 넣지않았을 때 기본값을 지정해줄 수 있다.
    ```
17. Index
    - Index는 데이터의 주소를 가지고 있다. 빠르게 데이터 작업을 하기위한 하나의 방법으로 사용된다
    - Primary Key, Unique설정시에 자동으로 index가 생성되지만, Foreign Key로 설정시에는 자동으로 index가 생성되지 않는다.
      ```
      -- index 직접 설정
      create index ex_index01 on userTbl(userId);
      -- index 삭제
      drop index ex_index01;
      ```
19. 트랜잭션
    ```
    CREATE TABLE TEST(NO NUMBER(3),NAME VARCHAR2(10),AGE NUMBER(3),GENDER VARCHAR2(6));

    INSERT INTO TEST VALUES(1, 'JOKER', '28', 'M');
    INSERT INTO TEST VALUES(2, 'ADAMS', '33', 'M');
    savepoint s1;
    INSERT INTO TEST VALUES(3, 'SMITH', '35', 'M');
    rollback to s1; -- 3번이 입력되기 전으로 rollback된다.
    rollback; -- 가장 최근 commit한 시점으로 rollback한다. 모든 입력을 넣기 전으로 돌아간다.
    INSERT INTO TEST VALUES(1, 'JOKER', '28', 'M');
    INSERT INTO TEST VALUES(2, 'ADAMS', '33', 'M');
    commit; -- 데이터베이스에 저장
    INSERT INTO TEST VALUES(3, 'SMITH', '35', 'M');
    rollback; -- 1,2번을 저장한 시점으로 롤백된다.
    drop table TEST PURGE; -- 테이블자체를 drop을 통해 삭제시킨 경우 롤백이 불가능하다.
    ```
21. 조인
    - inner join
    ```
    select * from usertbl inner join buytbl on usertbl.userid = buytbl.userid;
    -- on을 통해 join의 기준을 설정
    select userId,name,prodname,groupname from usertbl inner join buytbl on usertbl.userid = buytbl.userid;
    -- userId를 join하는 테이블이 모두 가지고 있으므로 에러가 발생한다.
    select usertbl.userId,name,prodname,groupname from usertbl inner join buytbl on usertbl.userid = buytbl.userid;
    -- 따라서 어느 테이블의 userId인지 명시해야한다.
    select U.userId,name,prodname,groupname from usertbl U inner join buytbl B on U.userid = B.userid;
    -- from절에서 테이블의 별칭을 지정하고 select,on에 이를 적용할 수 있다.
    select U.userId,price,amount from usertbl U inner join buytbl B
    on U.userid = B.userid where amount >= 5 order by amount desc;
    ```
    - outer join
    ```
    -- left OuterJoin
    -- userTbl을 기준으로 userTbl에 존재하는 userId와 같은 buyTbl의 행이 join된다.
    select * from userTbl U left outer join buyTbl B on U.userId = B.userID;
    
    -- right OuterJoin
    -- buyTbl을 기준으로 buyTbl에 존재하는 userId와 같은 userTbl의 행이 join된다.
    select * from userTbl U right outer join buyTbl B on U.userId = B.userID;
    ```
23. View
    - 자주 사용할 것 같은 테이블의 일부를 view라는 가상 테이블로 만들어 필요한 부분만을 사용하는 방식.
    ```
    create or replace view view_01 as select userId, name, concat(mobile1,mobile2) as phone from userTbl;
    -- view_01이라는 이름의 view가 없으면 생성하고 있다면 해당 내용으로 변경한다.

    create or replace view view_02 as select U.userId, U.name, B.prodname, B.amount as phone
    from userTbl U inner join buyTbl B on U.userId = B.userId;
    -- view와 join을 함께 사용

    select amount from view_02 where amount >=10;
    -- view_02의 쿼리가 서브쿼리의 형태로 주어진다.
    select amount from (select U.userId, U.name, B.prodname, B.amount as phone from userTbl U inner join buyTbl B on U.userId = B.userId);
    
    -- 따라서 table이 변경되면 view도 영향을 받는다.
    drop table buyTbl;
    select * from view_02; -- error!
    drop view view_01; -- view 삭제
    ```
25. PL&SQL
26. 프로시저
27. 트리거




























