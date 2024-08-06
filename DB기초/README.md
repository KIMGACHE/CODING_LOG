# Database

## DB기초
DB(DataBase) : 데이터의 저장소 <br>
Data : 자료, 피연산자, 저장이 되는 것들 중 가장 낮은 수준 <br>
ex) 김병관이라는 객체가 가진 자료들 (나이,키,주소,키 등등) <br>
**DBMS** : 데이터베이스를 운영하고 관리하는 소프트웨어이다. 대부분은 관계형 DBMS 형태로 사용된다. <br>
<br>

**정보피라미드 구조**
1. **지혜** : 지식에 유연성을 더하고 상황과 맥락에 맞는 규칙을 적용하는 것을 의미
2. **지식** : 정보를 일반화하고 체계화하여 적용, 활용할 수 있도록 만든것을 의미
3. **정보** : 자료들 중에서 사용자에게 필요한 데이터, 필요에 따라 가공된 데이터를 의미
4. **자료** : 가공되지 않은 관찰, 측정을 통해서 수집된 값, 수치, 문자등을 의미

<br>

예제) <br>
자료 -> <br>
A마트 : 라면10원, 빵5원, 우유 20원 <br>
B마트 : 라면11원, 빵7원, 우유 23원 <br>
<br>
정보 -> 라면이 B마트보다 A마트가 더 싸다.<br>
지식 -> A마트가 B마트보다 라면이 1원 더 싸므로 A마트에서 라면을 구매할 것이다.<br>
지혜 -> A마트가 B마트보다 대체적으로 가격이 저렴할 것으로 예상된다.<br>

<br>

## SQL 기본
**CRUD** : Create, Read, Update, Delete <br>
<br>
**DDL(Data Definition Language)** : 데이터 구조를 정의하는 언어 (create, alter, drop, truncate 등등)<br>
**DML(Data Manipulation Language)** : 데이터 구조에 입력된 데이터를 조회, 수정, 삭제 등의 역할을 하는 언어 (select, insert, update, delete 등등)<br>
**DCL(Data Control Language)** : 데이터베이스에 접근하는 권한에 관한 언어(grant, revoke 등등) <br>
**TCL(Transaction Control Language)** : Transaction을 제어하는 언어 (Commit, Rollback 등등)<br>

<br>

**DB 생성 및 삭제** <br>
생성 : create database DB명; <br>
삭제 : drop database DB명; <br>

**Table 생성 및 삭제** <br>
생성 : create DB명.Table명 ( Column명 데이터타입 제약조건 ); <br>
```
create test1db.tbl_user (
  user_id varchar(45) primary key,
  user_name varchar(45) not null
);
```
삭제 : drop DB명.Table명; <br>

**Table 수정** <br>
1. Column 추가
   alter table DB명.Table명 add column column명 데이터타입 제약조건;
   ```
   alter table test1db.tbl_user add column age int null;
   ```
3. Column 삭제
   alter table DB명.Table명 drop column column명;
   ```
   alter table test1db.tbl_user drop column age;
   ```
5. Column 수정
   alter table DB명.Table명 change column 기존column명 수정할column명 데이터타입 제약조건;
   ```
   alter table test1db.tbl_user change column user_name name varchar(45) not null;
   ```
<br>
**Table 값 입력** <br>
insert into 테이블명 (넣을 열) values (넣을 값);
```
insert into tbl_user (user_id, name, age, user_address) values ('user1', '홍길동', 27, '대구');
```
꼭 모든 열을 적을 필요는 없고 필요한 열과 필요한 값만 넣어도 된다. <br>
혹시 모든 열에 다 값을 넣을거라면 (넣을 열)을 생략하고 values 뒤에 열 순서대로 넣어주면 된다.
```
insert into tbl_user values ('user2', '남길동', 25, '대구');
```
<br>
**Table 값 수정** <br>
update 테이블명 set 수정할 열 = 수정할 값 where 조건;
```
update tbl_user set name='서길동' where user_id = 'user1';
```
<br>
**Table 권한부여** <br>
1. User 조회
```
show databases;
use mysql;
show tables;
select host, user from user;
```
2. User 생성
create user 유저명 identified by '비밀번호'; <br>
내 컴퓨터 기준 - localhost
```
create user user2@localhost identified by '1234';
create user user3@'%' identified by '1234';
```
3. 권한 부여
grant 권한을 줄 명령어 on 권한을 줄 DB.권한을 줄 Table명 to 권한을 줄 유저;
```
grant select, insert on test1db.* to user3@localhost;
grant all privileges on test1db.* to user3@localhost; - 모든 권한을 부여할 때
```
부여된 권한을 확인하고 싶을 때
```
show grant for user3@localhost;
```
부여된 권한을 적용하고 싶을 때
```
flush privileges;
```



































