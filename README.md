# CODING_LOG
정보처리산업기사 과정평가형 수업내용 기록 <br>
|목차|NCS모듈| | |
|:---|:---|:---|:---|
|SW_BASIC|[네트워크](./SW_BASIC/네트워크)|[미들웨어](./SW_BASIC/미들웨어)|[DB기초](./SW_BASIC/DB기초)|
|개발자 환경구축|[운영체제 기초](./개발자_환경구축/리눅스)|[GIT](./개발자_환경구축/GIT)||
|화면기획|[요구사항분석](./화면기획/요구사항분석)|[유스케이스](./화면기획/유스케이스)|[유스케이스명세서](./화면기획/유스케이스명세서)|
|화면구현|[HTML](./화면구현/HTML)|[CSS](./화면구현/CSS)|[JAVASCRIPT](./화면구현/JS)|
|응용SW엔지니어링|[JAVA](./프로그래밍언어/JAVA)|[JAVA2](./프로그래밍언어/JAVA2)|[JAVA3](./프로그래밍언어/JAVA3)|
|DB엔지니어링|[Oracle](./DB엔지니어링/ORACLE)|||

오라클 DB접속방법
cmd - sqlplus를 입력하면 - 계정과 비밀번호를 입력하면된다(system/1234)
workbench - 왼쪽상단에 +표시를 눌러서 DB를 새로 생성한다.

select name from v$database; -> db이름이 나옴
create user test_ex identified by 1234; -> test_ex라는 계정을 생성함 비밀벊로 1234
grant connect,dba to test_ex; -> test_ex에 권한부여

DB우클릭해서 워크시트 열기하면 입력창나옴
와일드카드 % : 문자수제한없이 모든
          _ : 문자수제한있는 모든

여러개의 값들중 선택해줘야할때
any : or연산
all : and연산

create table tbl_buy as select * from buyTbl; -> table을 생성 값과 구조를 모두 복사해옴
create table tbl_buy2 as select * from buyTbl where 1=2; -> where절에 일부러 false값을 받도록하여 구조만 복사해온다.

insert into tbl_buy2 select * from buytbl; -> 구조가 동일하다는 가정하에 select된 값을 그대로 넣어준다.

select name , mDate from usertbl order by mDate;-> order by 기준 으로 기본값 오름차순으로 정렬, desc를 뒤에 넣어서 내림차순도 가능 (사전편찬순)
select name,mDate,height from userTbl order by height desc, name asc; -> 중복된 녀석이 있을경우 name을 기준으로 오름차순 정렬
select distinct height from usertbl order by height; -> 중복해제

select rownum as RN, usertbl.* from usertbl; -> as는 별칭 지정 / rownum을 부여하는데 그 대상이 usertbl의 모든 값들? 이란 의미인듯

select * from
(select rownum as RN, usertbl.* from usertbl)
where RN >= 3;

-- userId별 구매 총량을 출력
select userid,sum(amount) from buytbl group by userid / 기본키는 들어가지않는게 좋다

select count(*) from buytbl; // count(*)는 null을 포함하지않는다 or count자체가 null을 포함하지않는다

select trunc(avg(amount),5) from buytbl -> 소숫점 5번째자리까지 출력

group by로 묶여지는 컬럼에대한 연산은 having을 사용해야만한다.

create sequence tmp_seq start with 1 increment by 1 maxvalue 100 cycle nocache; -> 1부터 시작해서 100까지 1씩 증가하는 tmp_seq작성

insert into tmp values(tmp_seq.nextval,'a1');          // seqeunce를 사용하여 auto increment를 대체

create table TEST_01 (
    userid char(10) primary key,
    name char(10) not null
);
desc TEST_01;
select * from all_constraints where TABLE_NAME = 'TEST_01' and CONSTRAINT_TYPE='P';
select * from ALL_CONS_COLUMNS where TABLE_NAME='TEST_01';

create table TEST_02 (
    userid char(10),
    name char(10) not null,
    primary key(userid)
); 
select * from all_constraints where TABLE_NAME = 'TEST_02' and CONSTRAINT_TYPE='P';
select * from ALL_CONS_COLUMNS where TABLE_NAME='TEST_02';

alter table TEST_01 drop primary key; -> 기본키 삭제하기
select * from all_constraints where TABLE_NAME = 'TEST_01' and CONSTRAINT_TYPE='P';
select * from ALL_CONS_COLUMNS where TABLE_NAME='TEST_01';

alter table TEST_01 add constraint PK_USERID primary key(userid); -> 기본키 추가하기


































































































