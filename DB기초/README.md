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
삭제 : drop DB명.Table명;














































