---
# 📝SQL
---
### # 데이터 베이스란?
>* 막대한 데이터를 관리하기 위하여 체계적으로 만든 것 , 컴퓨터가 다룰수 있는 용어로 변환시킨것
* 체계화된 데이터의 모임
* 방대한 데이터를 효율적으로 관리!!
* 여러 응용 시스템들의 통합된 정보를 저장하여, 운영할 수 있는 공용 데이터의 묶음
* DBMS: 데이터베이스를 관리하는 시스템 Realtional(관계형) Database Management System)
* 장점
    1. 데이터 중복 최소화
    2. 데이터 공유
    3. 일관성,무결성,보안성 유지
    4. 최신의 데이터 유지
    5. 데이터의 표준화 불가능
    6. 데이터의 논리적, 물리적 독립성
    7. 용이한 데이터 접근
    8. 데이터 저장 공간 절약
* 단점
   1. 데이베이스 전문가 필요
   2. 많은 비용 부담
   3. 시스템의 복잡함

---
### # SQL(Structured Query Language)
---
>* 관계형 데이터 베이스를 다루기 위해 알아야 함
* 관계형 데이터베이스 관리 시스템에서 데이터를 관리하기 위해 사용되는 표준 프로그래밍 언어
  * 데이터 정의 언어(DDL, Data Definition Language) : 데이터 구조 정의
    * 테이블, 인덱스 등의 개체를 만들고 관리하는데 사용되는 명령
  * 데이터 처리 언어 (dml)
    * 데이터 CRUD(create생성,read읽기,update갱신,delete삭제)
  * 데이터 제어 언어
        * 테이블 (Table) = 관계(Relation)
        * 컬럼(column) =필드 (Field) = 속성 (attribute)
        * 로우(Row) = 레코드(Record) = 튜플(tuple)

### * 숫자함수
        * ROUND() 반올림
        * CEIL(): 올림
        * FLOOR : 반올림
        * ABS () : 절대값
        * GREAST (): 괄호안에서 제일 큰값
        * LEAST() : 괄호안에서 가장 작은값
        * TRUNCATE(1234.5677, x) : x의 소수점에서 짤라냄

### * 문자함수
        * UCASE,UPPER : 모두 대문자로
        * LCASE,LOWER : 모두 소문자로
        * CONCAT('','+','') 문자열 신경안쓰고 하나의 문자열로
        * CONCAT_WS('x','','+',') : x 사이의 기준으로 하느이 문자열로 ,ex) SELECT CONCAT_WS(' ',FirstName,LastName) AS FullName FROM employees
        * SUBSTR (문자열,시작,끝) 시작점이 3이면 3번째 부터 읽는단 소리임
        * TRUNCATE(1234.5677, x) : x의 소수점에서 짤라냄
        * LEFT(문자열,4) 왼쪽에서 4개
        * RIGHT(문자열,4) 오른쪽에서 4
        * LENGHT(문자열,x) 문자열의 바이트 길이
        * CHAR_LENGHT(문자열,x) 문자열의 길이 : 주로이거 쓸듯
        * LPAD('abc',5','-') abc 의 글자가 5글자가 될댸까지 마지막 글자를 붙여씀 왼쪽에
        * RPAD('abc',5','-') 오른쪽에
        * REPLACE ( 'abc db abc','db','ac') db 가 ac 로 나옴 안에있는 db 전부 , 쉼표를 and 로 바꿀때 이럴때 사용

### * 날짜 함수
        * CRURRENT_DATE,CURDATE() : 현재 날짜 반환
        * CURTIME() :현재시간
        * NOW,CURRENT_TIMESTAMP : 현재 시간과 날짜 반환
        * DATE,TIME : 문자열에 따라 생성
        * DATE_ADD,DATE_SUB
        * DATEDIFF(테이블,NOW())m,TIMEDIFF
---
### SQL 용어
---
    * PRIMARY KEY : 한 테이블의 각 로우를 유일하게 식별해주는 용어
       - 각 테이블마다 PRIMARY KEY 는 꼭 존재해야하고, NULL 값을 허용하지 않고 ,ROW(행,레코드)마다 유일한 값이어야한다.
    * FOREIGN KEY : 한 테이블의 컬럼 중 다른 테이블의 로우를 식별할수있는 키
      - FOREGIN KEY (칼럼명) REFERENCES 호출될테이블명 (그테이블의칼럼명)
      - 데이터의 중복성을 최소화 , 물건을 살거야 근데 사는 사람은 같고 그사람 정보는 같자나 근데 매버 다른 물품을 사는거지 그럴때마다 사는사람 정보는 동일한대 적을필요가 없다는거지 그래서 userid 를 foreign 키로 넣고 그 키를 통해 그 사람의 인적사항을 불러들일수 잇는거지,
      - FOREIGN KEY 가 설정되 있는값에 INSERT INTO 로 넣을려면 FOREIGN KEY 로 연결되어 있는 테이블에 그사람의 정보가 있어야 더 추가해서 넣을수 있다 삿는데 그사람이 등록이 안돼있대? 그럼 이상하자나 먼저 등록을 하고 추가하는거지 부모에 먼저 넣는다 생각해
      - 데이터 무결성(이론적으론 두테이블간 관계에 있어서 데이터 정확성을 보장하는 제약 조건을 넣는거임)
      - DELETE FROM userTbl WHERE userID = --- 이렇게 삭제할라는 개 만약 FOREIGN KEY 와 연결되어 있는 칼럼이면 삭제가 안된다 연결되어있는걸 먼저 삭제 시켜야 삭제가됨 연결되어있는 곳에서 FOREGIN KEY 가 연결되어있는 id 를 먼저 삭제해야함
    * DECIMAL(정수부 길이,소수점 자릿수) 
    * TINYINT -128~ 127 이 보통인데 0~+255 쓰려면 id TINYINT UNSIGHNED 옵션을 넣어주자
    * NOT NULL : 반드시 값이 있어야대 라는 제약조건 옵션을 달아주는 것 , 칼럼 데이터에 값이 할당되지 않으면 실행안됨
    * AUT0_INCREMENT : 프라이머리 키에 모든것을 확인 하기 어려워서 보통 프라이머리 키에 옵션을 추가해줌 PRIMARY KEY(id) 레코드,로우를 넣을때마다
      지금까지 넣은 AUTO_INCREMENT 가 지정된 컬럼에 지금까지 사용된 최대값을 찾고 자동으로 그다음 숫자를 넣어줌
    * CHAR(n) : 고정 길이 데이터 타입, 정확히 사용 3글자만 적어도 n만큼 낭비가 되버림
    * VARCHAR(n) : 정해주는건 똑같지만 실제 데이터엔 적은 글자만큼만 적어짐 그래서 실제 데이터 낭비가 안나옴
        # 저장이 되고 난후에 데이터를 바꾸는데 저장해논 글자보다 큰경우 굉장히 난해해짐  수정할일이 없는 데이터에 이 데이터 유형을 쓰면됨
---
### SQL 문법
---
    * CREATE SCHEMA 데이터베이스명 = CREATE DATABASE 데이트베이스명
    * CREATE TABLE : 테이블 명을 만들때 안에 객체 넣어줄때 모든 값은 타입을 넣어줘야한다
    * SHOW TABLES,DATABASES : 생선된 테이블명 데이터베이스 명 보기
    * DESC 테이블명 : 테이블 안의 설정 보기
    * DROP 테이블명 : 테이블 삭제
    * GROUP BY : 특정 칼럼값을 기반으로 그룹핑하기 , 무슨 각 등급별, 각 시간별 이런느낌이면 그룹핑?
    * HAVING 절은 집계함수를 가지고 조건비교를 할 때 사용
     - HAVING 절은 GROUP BY절과 함께 사용
        - SELECT 컬럼명 FROM 테이블명 GROUP BY 컬렴명 HAVING COUNT(*) >,=,<... 숫자;  
          이런식으로 사용
          원래 조건은 WHERE COUNT(*) 쓰는건데 집계함수를 GROUP BY 랑 같이 쓰지를 못한다 그래서 HAVING 절을 쓰는것
          HAVING 절은 무조건 GROUP BY 뒤에 걍 쓰면됨 WHERER 절이랑 카운터를 같이 못써서 그럼
    

* 테이블 변경 명령 -> ALTEAR TABLE 테이블명 MODIFY,ADD,CHANGE,DROP COLUMN ~~
 - 테이블에 새로운 컬럼 추가 <br>
 ```sql
 문법: ALTER TABLE [테이블명] ADD COLUMN [추가할 컬럼명][추가할 컬럼 데이터형] 
mysql> ALTER TABLE mytable ADD COLUMN model_type varchar(10) NOT NULL;
 ```
 - 테이블 컬럼 타입 변경
 ```sql
문법: ALTER TABLE [테이블명] CHANGE COLUMN [기존 컬럼 명][변경할 컬럼 명][변경할 컬럼 타입]
mysql>ALTER TABLE mytable CHANGE COLUMN modelnumber model_num varchar(10) NOT NULL;
```
 - 테이블 컬럼 이름 변경
  ```sql
문법: ALTER TABLE [테이블명] CHANGE COLUMN [기존 컬럼 명][변경할 컬럼 명][변경할 컬럼 타입]
mysql>ALTER TABLE mytable CHANGE COLUMN modelnumber model_num varchar(10) NOT NULL;
```
 - 테이블 컬럼 삭제
  ```sql
문법: ALTER TABLE [테이블명] DROP COLUMN [삭제할 컬럼 명]
mysql>ALTER TABLE mytable DROP COLUMN series;
```
* Create,Read,Update,Delete
* INSERT
        * 테이블 전체 칼럼에 대응하는 값을 모두 넣기
            * INSERT INTO 테이블명 VALUES(값 1,값2....)  -> 컬럼에 해당하는 것들전부 넣어야되지만
        * 테이블 특정 컬럼에 대응하는 값만 넣기
            * INSERT INTO 테이블명 (col1,col2,...) VALUES(값1,값2,...) col1 값 1 대응, 값을 추가할때 추가하고 싶은 컬럼에만 넣으면댐
* **데이터 읽기(검색) SELECT**
        * 테이블 전체 컬럼의 데이터 모두 읽기
         - SELECT * FROM 테이블명 ;
        * 테이블 특정 컬럼의 데이터만 읽기
         - SELECT 컬럼1,컬럼2 FROM 테이블명;
 * **조건문 WHERE**
    * SELECT * FROM students WHERE age = 16; 16살 인사람만
            * !=,<,>,<=,>= 비교연산자,파이썬이랑 다른점은 같다 ==가 아니라 = .
            * 논리연산자도 사용가능 WHERE age >=15 AND grade='10학년' 이런식으로 가능 ,NOT 가능
            * LIKE 문자열 데이터 검색기능
            * % : 0개이상의 문자를 대체 WHERE name LIKE '박%'; ->박으로 시작하는 문자열,'%민%'--> 민이라는 문자열이 있으면 출력
            * _ : 단일 문자를 대체 WHERE name LIKE '\_민_\'; 민 앞뒤로 한글자만 있으면 출력 _는 앞에 하나만있으며언~ 인듯 ,'\___\' 이렇게 있으면 3글자단어 전부출력\
* **데이터 수정 UPDATE**
    * UPDATE 테이블명 SET 컬럼명 ='새로운값' WHERE 조건;
     - 조건을 안쓰면 모든 컬럼명이 바꾸는데 이렇게 쓰는경우는 보통없음, 조건에 보통 PRIMARY KEY 을 넣고 사용함
    * UPDATE 테이블명 SET 컬럼명1 = '값1', 컬렴명2 ='값2' WHERE 조건; 여러 칼럼이 틀린경우 한줄로 저렇게 작성 가능 대응 주의해서 사용
---
### # SELECT
---
>1. SQL SELECT 문법1: LIMIT 
   * 일부 데이터만 가져오는 기능 (현업에서 너무 낳은 데이터를 가져오면 시간이 너어어무 걸림)
     - SELECT * FROM 테이블명 LIMIT 10 : 테이블 데이트 중 __최상위에 있는 10개의 데이터만 가져오기__
     - SELECT * FROM 테이블명 WHERE 조건문 LIMIT 1: 특정 조건에 맞는 데이터 중 최상위에 있는 1개의 데이터 가져오기
2. SQL SELECT 문법2: COUNT
   * 결과 수 세기
     - SELECT COUNT(*) FROM 테이블이름 : 테이블 전체 데이터 수 세기
     - SELECT COUNT(*) FROM 테이블이름 WHERE 조건문 : 조건에 맞는 테이블 데이터 수 세기
3. SQL SELECT 문법3: DISTINCT
   * 특정 컬럼값 출력시 중복된 값을 출력하지 않음 ( 범주형 데이터에서 그 종류가 무엇이 있는지 파악할때 사용, 한칼럼에서 쓰인 값들이 뭔지 파악할수 있음 )
     - SELECT DISTINCT 컬럼명 FROM 테이블이름 : 특정 컬럼에 들어가 있는 컬럼 종류 확인하기
     - SELECT DISTINCT 컬럼명 FROM 테이블이름 조건문 : 특정 조건에 맞는 특정 컬럼에 들어가 있는 종류 확인하기)

>4. SQL SELCET 문법4: SUM,AVG,MAX,MIN
   * SELECT SUM(컬럼명) FROM 테이블이름
   * SELECT AVG(컬럼명) FROM 테이블이름 WHERE 조건
     - SELECT SUM(),AVG(),MAX() FROM 테이블명 이렇게 한번에 구할수도있음
5. SQL SELECT 문법 5: GROUP BY 
   * 특정 칼럼값을 기반으로 그룹핑하기 , 무슨 각 등급별, 각 시간별 이런느낌이면 그룹핑?
     - SELECT rating FROM film GROUP BY rating (필름 테이블의 rating 값을 그룹핑해라, 즉 rating 값별로 출력하므로, rating 값 종류를 확인 할 수 있음 ,각각의 그룹별로 레이팅값을 영화에서 보여달라)
     - SELECT COUNT(*) FROM film GROUP BY rating (각 rating 값 종류별로 몇개의 데이터가 있는지 확인)
     - SELECT COUNT(*) FROM film WHERE 조건 GROUP BY rating (조건에 맞는 데이터 중 rating 값 종류별로, 몇개의 데이터가 있는지 확인)
     - ex SELECT rating,COUNT(*),AVG(rental_rate) FROM film GROUP BY rating <br> rating 별로 묶인 레이팅의 종류,몇개,평균은 몇인가를 구하는 것

>6. SQL SELECT 문법 6 : ORDER BY
   * 특정 칼럼값을 기준으로 데이터 정렬하기
     - ORDER BY 정렬할 기준 컬럼명 DESC또는ASC
       - SELECT * FROM film ORDER BY rating DESC : rating 값을 기준으로 내림차순으로 정렬해라
       - SELECT * FROM film ODRER BY rating ASC : 오름차순으로 정렬해라
       - SELECT * FROM film WHERE 조건문 ORDER BY rating ASC 조건에 맞는 데이터를 rating 값을 기준으로 올림차순으로 정렬해라
       - SELECT COUNT(*) FROM film WHERE 조건문 GROUP BY 컬럼 ORDER BY COUNT(*) ASC
         <br> 조건에 맞는 데이터를 특정 칼럼값을 기준으로 그룹핑하되, rating 값을 기준으로 올림차순으로 정렬해라
       - 오더바이 뒤에가 또 조건이라 생각 평균값을 기준으로~ 주로 숫자에쓰일듯?
     - DESC ASC 명시 안하면 ASC 로 정렬
7. SQL SELECT 문법 7 : AS
   * 표시할 칼럼명도 다르게 하기
     - SELECT COUNT(*) AS total FROM film (AS 빼도 됨 근데 가독성!!)
---
### # JOIN
---
        * 2개 이상의 테이블로부터 필요한 데이터를 연결해 하나의 포괄적인 구조로 결합시키는 연산
        * 세분화 될 수 있지만 보통은 INNER JOIN 을 많이 사용함
         - INNER JOIN(일반적인 JOIN) : 두 테이블에 해당 필드값이 매칭되는 (두 테이블의 모든   
           필드로 구성 된) 레코드만 가져옴
         - OUTER JOIN 
          + LEFT OUTER JOIN : 왼쪽 테이블에서 모든 레코드와 함께, 오른쪽 테이블에 왼쪽 테이블 
            레코드와 매칭되는 레코드를 붙여서 가져옴
          + RIGHT OUTER JOIN : 오른쪽 테이블에서 모든 레코드와 함계, 왼쪽 테이블에 왼쪽 테이블 
            레코드와 매칭되는 레코드를 붙여서 가져옴
1. JOIN(INNER JOIN)
   * SELCET * FROM 1번테이블 INNER JOIN 2번테이블 ON 왼테이블.컬럼=오른테이블,컬럼(조건) : 매칭되는 것만 합쳐지고 나머진 안합쳐짐,조건이 맞는 양쪽꺼
     <br> 이렇게 합친 테이블을 가지고 뒤에 WHERE 이나 조건을 써서 찾는 것 (조건을 쓸때 어느 테이블인지 쓰려면 테이블.컬럼명 이렇게 사용)
    - ```sql
      SELECT * FROM items INNER JOIN ranking ON ranking.item_code = items.item_code WHERE ranking.main_category = "ALL"
      ```
    - ```sql
      SELECT * FROM items a INNER JOIN ranking b ON a.item_code = b.item_code WHERE b.main_category = "ALL"
      ``` 
      AS 구문처럼 a 로 짧게 바꿔서 쓸 수 있음, 뒤에 짧게 짧게 쓸수있음, 가독성을 위해 각글자의 대문자를따보자 같으면 2번째글짜까지

2. OUTER JOIN
   - OUTER JOIN 은 조인하는 테이블의 ON 절의 조건 중 한쪽의 데이터를 모두 가져옴
   - LEFT OUTER JOIN, RIGHT JOIN 두가지 종류가 있음 (왼쪽꺼 다가져오기 ,오른쪽꺼 다가져오기 나머지부분은 빈부분은 NULL )
---
#### # 서브쿼리
---
        * SQL 문 안에 포함되어 있는 SQL 문 : SQL 문 안에서 ()를 사용해서 서브쿼리문을 쓸수있음
        * 테이블과 테이블간의 검색시 검색범위(테이블 중 필요한 부분만 먼저 가져오도록)를 줄이는 기능에 주로 사용 , JOIN 이랑 비슷한 기능인데 다른방법 주로JOIN씀
        ex) 
        ```sql
        SELECT title
        FROM items
        INNER JOIN ranking ON items.item_code = ranking.item_code
        WHERE ranking.sub_category =
        '여성신발'
        같음
        SELECT title
        FROM items
        WHERE item_code IN
        (SELECT item_code FROM ranking WHERE sub_category =
        '여성신발')
        * 같은 조건이 있어야만 쓸 수 있다
        ```
1. 조건에 맞는 것쿼리 에 해당하는 테이블입력
2. 공통 조건 WHERE 선언 그후 IN 
3. 안에서 SELECT 공통조건 FROM 다른테이블 WHERE 마지막조건)
* 두테이블 간의 조건이 있을때 서브쿼리 사용할수도 있다.
* JOIN 을 주로 쓰자
---
### # 인덱스 
---
* SHOW INDEX FROM 테이블명 : 인덱스가 PRIMARY KEY 로 적혀있는게 클러스터형 인덱스,Key_name 이 자기 컬럼명으로 되있으면 보조키임
  <br>FOREIGN KEY 로 설정된 컬럼이 인덱스가 없다면, 보조 인덱스를 자동 생성
        * 데이터베이스 분야에 있어서 테이블에 대한 동작의 속도를 높여주는 자료 구조
        * 어떤 데이터를 인덱스로 만드느냐에 따라 방대한 데이터의 성능에 큰 영향을 미칠 수 있음
* 인덱스 종류
        1. 클러스터형 인덱스: 영어 사전과 같은 형태로 데이터를 재정렬하여 저장한다 생각,
         - 테이블의 데이터를 실제로 재정렬하여 디스크에 저장
         - 테이블에 PRIMARY KEY 로 정의한 컬럼이 있을 경우 자동 생성
         - 한 테이블당 하나의 클러스터형 인덱스만 가질 수 있음
        2. 보조 인덱스 : 데이터는 그대로 두고, 일반 책 뒤에 있는<찾아보기> 와 같은 형태가 만들어진다 생각
         - 클러스터형 인덱스와 달리 데이터를 디스크에 재정렬 하지않고 각데이터의 위치만 빠르게 찾을  
           수 있는 구조로 구성
         - 보조 인덱스를 저장하는데 필요한 디스크 공간은 보통 테이블을 저장하는데 필요한 디스크     
           공간보다 작음
         - 인덱스는 키-필드만 갖고 있고, 나머지 세부 테이블 컬럼 정보는 가지고 있지 않기 때문

---
## # pymysql 사용하기
---
```python
# 1. 데이터베이스 불러오기
import pymysql 
db = pymysql.connect(  ##접속 edit 하면 나오는것 입력
host='localhost', # 127.0.0.1 , 0.0.0.0 
port=3306, 
user='root', # root 이
passwd='0000', #비밀번호 입력 
db='데이터베이스명', #연결할 database 명 워크밴치에 있어야댐!!
charset='utf8'

# 2. 커서 가져오기
cusror = db.cursor()
# 3. sql 테이블 만들기
sql = """
   CREATE TABLE product (
   PRODUCT_CODE VARCHAR(20) NOT NULL,
   TITLE VARCHAR(200) NOT NULL,
   ORI_PRICE INT,
   DISCOUNT_PRICE INT,
   DISCOUNT_PERCENT INT,
   DELIVERY VARCHAR(2),
   PRIMARY KEY(PRODUCT_CODE)
   );
   """  #<- 워크밴치 에서 처럼 생성 sql 생성
# 4. sql 구문 실행하기
cursor = db.cursor(sql)
# 5. sql complete ,SELECT 구문은 새로 고친것이 없기에 사용하지 않는다.
db.commit()
# 6. 종료
db.close()
```
* 데이터 삽입 
```python
# 2번까지 동일
# 테이블을 값 만드는 코드 작성
for i in range(10):
    product_code = 215673140 + index + 1
    SQL = """
    INSERT INTO product VALUES
        ('""" + str(product_code) + """',
        '스위트바니 여름신상5900원~롱원피스티셔츠/긴팔/반팔', 23000, 6900, 70, 'F'
        );
    """
    print(SQL)
    cursor.execute(SQL) # 실행
```
* 데이트 조회 코드 (SELECT) 
 - fetchall() : 쿼리 결과의 모든행 , 결과는 튜플로 반환 ,각내부 튜플은 하나의 레코드 반환
 - fetchone() : 한줄, 실행될때마다 다음줄로 넘어가서 반환 , 끝나면 None
 - fecthmany(size) : size 줄 만큼
 ```python
 cursor.execute("SELECT * FROM 테이블명")
 rows = cursor.fetchall()
 for row in rows:
    print(row)
 ,
 row = cursor.fetchone()
 while row is not None :
    print(row)
    row=cursor.fetchone()
 ``` 

---
#### 파이썬 크롤링
---
```python
import pymysql

db = pymysql.connect(
        host='localhost', # 127.0.0.1 , 0.0.0.0 
        port=3306, 
        user='이름', # root
        passwd='패스워드', 
        db='연결할 데이터베이스 명', 
        charset='utf8')
cursor = db.cursor()
import requests
from bs4 import BeautifulSoup

for page_num in range(10):
    if page_num == 0:
        res = requests.get('https://000000/')
    else:
        res = requests.get('https://0000/page'+str(page_num+1))
    soup = BeautifulSoup(res.content,'html.parser')
    data = soup.select('div.00-00') #다가져오는것
    for 00 in 00 :
        00 = 00.00('00').get_text().replace('000','').strip()#없애는과정.
        00 = 00.select_one('00').get_text().replace('00:','').strip()
        print(category,product)
        SQL ="""INSERT INTO 00 (00,00) VALUES('"""+00+"""','"""+00+"""');"""
        print(SQL)
        cursor.execute(SQL)
        
db.commit()
db.close()

# SQL="""SELECT * FROM 00 WHERE CATEGORY = '00'; """
# SQL="""SELECT DISTINCT 00 FROM 00"""
SQL = """SELECT 00, COUNT(*) FROM 00 GROUP BY 00"""
cursor.execute(SQL)
rows=cursor.fetchall()
for row in rows:
    print(row) # row 인덱스 넣어서 가능

        
db.commit()
db.close()


```
---
## # Tip
---
* 테이블과 테이블 간의 관계
  - 다른테이블에 상세정보가 잇꼬 각정보를 구별할 수있는 id 값으로 연결되어 있는 경우가 많다.(하나의 테이블에 모든 정보를 안담음)
* 무슨 작업을 하던지 단계별로 하는것이 중요함
  1. payment 칼럼 리밋으로 확인
  2. payment 테이블 amount 칼럼에서 최소 합 평균 이런거 구하기 이런식
* **SQL 조건 순서 SELECT ->FROM -> WHERE -> GROUP BY -> ORDER BY -> LIMIT**
* WHERE 컬럼명 IN ('','','') 컬럼명의값이 '','','' 인것들 출력 IN

