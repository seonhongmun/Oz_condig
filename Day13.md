# 01. MySQL 기초

## SQL의 주요 언어 유형
1. **DDL (Data Definition Language)**: 데이터베이스의 구조를 정의하는데 사용되는 언어입니다.
    - **`CREATE`**: 새로운 테이블이나 데이터베이스 생성
    - **`ALTER`**: 기존 테이블이나 데이터베이스 구조 수정
    - **`DROP`**: 테이블이나 데이터베이스 삭제
2. **DML (Data Manipulation Language)**: 데이터베이스 내의 데이터를 처리하는 데 사용되는 언어입니다.
    - **`SELECT`**: 데이터베이스에서 데이터 조회
    - **`INSERT`**: 테이블에 새로운 데이터 추가
    - **`UPDATE`**: 테이블의 기존 데이터 수정
    - **`DELETE`**: 테이블에서 데이터 삭제
3. **DCL (Data Control Language)**: 데이터베이스 사용자의 권한을 관리하고 데이터 접근을 제어하는데 사용되는 언어입니다.
    - **`GRANT`**: 사용자에게 특정 데이터에 대한 접근 권한 부여
    - **`REVOKE`**: 사용자의 특정 데이터 접근 권한 제거
4. **TCL (Transaction Control Language)**: 데이터베이스 내의 트랜잭션을 관리하는데 사용되는 언어입니다.
    - **`COMMIT`**: 트랜잭션을 완료하고, 데이터베이스 변경사항을 영구적으로 저장
    - **`ROLLBACK`**: 트랜잭션을 취소하고, 마지막 **`COMMIT`** 이후의 모든 변경사항을 되돌림
    - **`SAVEPOINT`**: 트랜잭션 내 특정 지점을 마킹하여 필요시 그 지점으로 되돌릴 수 있음
각각의 언어 유형은 데이터베이스의 다양한 측면을 다루며, 데이터베이스의 구조를 정의하고(DDL), 데이터를 처리하며(DML), 사용자 권한을 관리하고(DCL), 트랜잭션을 제어하는(TCL) 역할을 합니다. 이러한 분류를 통해 데이터베이스 시스템의 효과적인 관리와 운영이 가능해집니다.

## MySQL User 데이터
- 관리자 권한: 유저와 관련된 작업을 수행하기 위해서는 MySQL에서 관리자(보통 root) 권한이 필요

> mysql -u root -p # 유저 로그인

1. mysql 유저 확인
mysql> USE mysql;
mysql> select * from user;

2. mysql 유저 생성
mysql> USE mysql;
mysql> CREATE USER 'username'@'localhost' IDENTIFIED BY 'user_password';

3. 사용자 비밀번호 변경
mysql> SET PASSWORD FOR 'username'@'%' = '신규비밀번호';

4. 권한 부여 (모든 데이터베이스에 대한 권한 부여)
> GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost';
> FLUSH PRIVILEGES; # 변경된 권한 적용
> SHOW GRANTS FOR 'username'@'localhost'; # 부여된 권한 확인
> SHOW GRANTS; # 현재 로그인한 유저의 권한 확인

5. 사용자 삭제
mysql> USE mysql;
mysql> DROP USER 'username'@'%';
```

## MySQL 데이터베이스 Schema 구성 (DDL)

### **CREATE TABLE [테이블명] 관련 명령어**

1. **PRIMARY KEY**
    
    테이블의 주요 식별자(primary key)를 정의합니다. 주로 유일성을 보장하고 검색 속도를 향상시키기 위해 사용됩니다.
    CREATE TABLE users (
        id INT PRIMARY KEY,
        username VARCHAR(50)
    );

1. **AUTO_INCREMENT**
    
    AUTO_INCREMENT는 숫자 자동 증가 속성을 가진 칼럼에 사용됩니다. 이 옵션을 사용하면 해당 칼럼의 값이 자동으로 1씩 증가합니다.
    CREATE TABLE users (
        id INT AUTO_INCREMENT PRIMARY KEY,
        username VARCHAR(50)
    );

1. **NOT NULL**
    
    NOT NULL 제약은 해당 칼럼에 NULL 값을 허용하지 않도록 합니다. 즉, 해당 칼럼에는 항상 값이 존재해야 합니다.

    	CREATE TABLE users (
        id INT AUTO_INCREMENT PRIMARY KEY,
        username VARCHAR(50) NOT NULL
    );

1. **UNIQUE**
    
    UNIQUE 제약은 해당 칼럼에 중복된 값을 허용하지 않습니다.

    CREATE TABLE users (
        id INT AUTO_INCREMENT PRIMARY KEY,
        username VARCHAR(50) NOT NULL,
        email VARCHAR(100) UNIQUE
    );

1. **DEFAULT**
    
    DEFAULT 옵션은 새로운 레코드가 삽입될 때 해당 칼럼에 지정된 기본값을 사용합니다.

    CREATE TABLE users (
        id INT AUTO_INCREMENT PRIMARY KEY,
        username VARCHAR(50) NOT NULL,
        email VARCHAR(100) UNIQUE,
        is_business VARCHAR(10) DEFAULT False
    );

1. **CHECK**
    
    CHECK 제약은 해당 칼럼에 저장될 수 있는 값의 범위나 조건을 지정합니다.

    CREATE TABLE users (
        id INT AUTO_INCREMENT PRIMARY KEY,
        username VARCHAR(50) NOT NULL,
        email VARCHAR(100) UNIQUE,
        is_business VARCHAR(10) DEFAULT False,
        age INT CHECK (age >= 18)
    );

CREATE TABLE users (
    user_id INT PRIMARY KEY,
    name VARCHAR(255),
    age INT
);
INSERT INTO users (user_id, name, age)
VALUES (1, 'Alice', 25),
       (2, 'Bob', 30),
       (3, 'Charlie', 22),
       (4, 'David', 33),
       (5, 'Eve', 28);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    user_id INT,
    order_date DATE
);
INSERT INTO orders (order_id, user_id, order_date)
VALUES (101, 1, '2023-01-01'),
       (102, 2, '2023-02-01'),
       (103, 1, '2023-02-15'),
       (104, 3, '2023-03-01'),
       (105, 4, '2023-03-10');
```

## MySQL 데이터 타입
| **숫자형** | **설명** |
| --- | --- |
| **`BIT(M)`** | 0과 1로 구성된 이진값, M은 1~64 사이의 값. |
| **`BOOL`** | 0은 false, 0이 아닌 값은 true로 간주되는 논리형 데이터. (true: 1) |
| **`TINYINT(M)`** | 1바이트 정수, 부호 있는 수는 -128 ~ 127, 부호 없는 수는 0 ~ 255. |
| **`SMALLINT(M)`** | 2바이트 정수, 부호 있는 수는 -32768 ~ 32767, 부호 없는 수는 0 ~ 65535. |
| **`MEDIUMINT(M)`** | 3바이트 정수, 부호 있는 수는 -8388608 ~ 8388607, 부호 없는 수는 0 ~ 16777215. |
| **`INT(M)`** 또는 **`INTEGER(M)`** | 4바이트 정수, 부호 있는 수는 -2147483648 ~ 2147483647, 부호 없는 수는 0 ~ 4294967295. |
| **`BIGINT(M)`** | 8바이트 정수, 부호 있는 수는 -92233720036854775808 ~ 92233720036854775807, 부호 없는 수는 0 ~ 18446744073709551615. |
| **`DECIMAL(M,D)`** 또는 **`NUMERIC`** | M자리 정수(정밀도)와 D자리 소수점(스케일)으로 표현. 최대 65자리까지 표현 가능. |

| **문자형** | **설명** |
| --- | --- |
| **`CHAR(M)`** | 고정 길이 문자열 저장 (M: 0 ~ 255). |
| **`VARCHAR(M)`** | 가변 길이 문자열 저장 (M: 0 ~ 65,535). |
| **`TINYTEXT`** | 1 ~ 255 길이의 가변 길이 문자열. |
| **`TEXT`** | 1 ~ 65,535 길이의 가변 길이 문자열. |
| **`MEDIUMTEXT`** | 1 ~ 16,777,215 길이의 가변 길이 문자열. |
| **`LONGTEXT`** | 1 ~ 429,496,729 길이의 가변 길이 문자열. |
| **`ENUM`** | 최대 65,535 개의 문자열 중 하나를 반환. |
| **`SET`** | 비트 연산 열거형, 문자열 값을 정수값으로 매핑하여 저장. |
- **`CHAR(M)`과 `VARCHAR(M)`의 차이**
    
### **CHAR(M)**
    
- **고정 길이 문자열 저장**: **`CHAR(M)`**은 항상 M개의 문자를 저장합니다.
- **길이 범위**: 0에서 255 사이의 길이를 가질 수 있습니다.
- **공간 사용**: M 길이의 고정 공간을 사용합니다. 저장된 문자열이 M보다 짧으면 나머지 공간은 공백으로 채워집니다.
- **사용 사례**: 길이가 일정하거나 변하지 않는 데이터에 적합합니다. 예를 들어, 성별, 국가 코드 등.

### **VARCHAR(M)**

- **가변 길이 문자열 저장**: **`VARCHAR(M)`**은 최대 M개의 문자를 저장할 수 있으며, 실제 저장되는 문자열의 길이에 따라 공간을 사용합니다.
- **길이 범위**: 0에서 65,535 사이의 길이를 가질 수 있습니다.
- **공간 사용**: 실제 문자열 길이에 따라 가변적인 공간을 사용합니다. 추가적으로, 문자열 길이를 저장하기 위한 1~2바이트의 추가 공간이 필요합니다.
- **사용 사례**: 길이가 예측 불가능하거나 변할 수 있는 데이터에 적합합니다. 예를 들어, 사용자 이름, 설명 텍스트 등.

### **차이점 요약**

- **길이**: **`CHAR`**는 고정 길이, **`VARCHAR`**는 가변 길이입니다.
- **공간 효율성**: **`CHAR`**는 항상 고정된 공간을 사용하지만, **`VARCHAR`**는 실제 데이터 길이에 따라 공간을 사용합니다.
- **적용 사례**: **`CHAR`**는 데이터 길이가 일정한 경우에, **`VARCHAR`**는 길이가 변할 수 있는 경우에 적합합니다.

| **날짜형** | **설명** |
| --- | --- |
| **`DATE`** | 날짜를 표현하는 타입 (3바이트), '1000-01-01' ~ '9999-12-31'. |
| **`DATETIME`** | 날짜와 시간을 같이 나타내는 타입 (8바이트), '1000-01-01 00:00:00' ~ '9999-12-31 23:59:59'. |
| **`TIMESTAMP`** | '1970-01-01 00:00:00' ~ '2037-01-19 03:14:07', INSERT, UPDATE 연산에 유리 (4바이트). |
| **`TIME`** | 시간을 표현하는 타입 (3바이트), '-838:59:59' ~ '838:59:59'. |
| **`YEAR`** | 연도를 나타냄 (1바이트), 1901 ~ 2155, 70 ~ 69 (1970 ~ 2069). |
- **`DATETIME`과 `TIMESTAMP` 의 차이**

## DATATIME 과 TIMESTAMP
DATETIME
- 범위: **`1000-01-01 00:00:00`**부터 **`9999-12-31 23:59:59`**까지.
- 저장 크기: 8바이트.
- 시간대에 무관: **`DATETIME`** 값은 시간대 변환 없이 그대로 저장됩니다.
- 사용 사례: 특정 사건이 발생한 정확한 시점을 기록할 때 사용. 예를 들어, 사용자의 생일이나 기념일 등.
TIMESTAMP
- 범위: **`1970-01-01 00:00:00`**부터 **`2037-01-19 03:14:07`**까지.
- 저장 크기: 4바이트.
- 시간대 인식: **`TIMESTAMP`**는 UTC로 저장되며, 조회 시 서버의 시간대 설정에 따라 변환됩니다.
- 자동 갱신: **`INSERT`**나 **`UPDATE`** 연산 시 현재 시간으로 자동 갱신될 수 있습니다.
- 사용 사례: 레코드의 생성 또는 수정 시간을 기록할 때 주로 사용. 예를 들어, 게시물의 작성 시간이나 마지막 수정 시간 등.
사용시 고려사항
- **시간대**: 국제화된 애플리케이션에서는 시간대 변환의 중요성 때문에 **`TIMESTAMP`**가 유리할 수 있습니다.
**범위와 저장 크기**: **`DATETIME`**은 더 넓은 범위를 커버하며 더 많은 저장 공간을 사용합니다.
**자동 갱신의 필요성**: 레코드의 생성 또는 수정 시간을 자동으로 추적하고 싶다면 **`TIMESTAMP`**가 적합합니다.
**`DATETIME`**은 시간대에 무관한 넓은 범위의 날짜와 시간을 8바이트로 저장
**`TIMESTAMP`**는 시간대를 인식하는 좁은 범위의 날짜와 시간을 4바이트로 저장하며, 자동 갱신 기능


## SQL (DML) 기초
### 테이블 생성 - CREATE TABLE (DDL)

CREATE TABLE users (
    user_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    username TEXT NOT NULL,
    email TEXT NOT NULL,
    age INTEGER
);

### 데이터 생성 - INSERT INTO
**1. 기본적인 INSERT 문**
가장 기본적인 형태로 모든 컬럼에 값을 지정하여 레코드를 추가합니다.

INSERT INTO users (username, email, age) VALUES ('john_doe', 'john@example.com', 25);

**2. 모든 컬럼에 값을 지정하지 않는 경우**
일부 컬럼에만 값을 지정하고 나머지는 기본값 또는 NULL 값을 가지도록 할 수 있습니다.

INSERT INTO users (username, email) VALUES ('jane_doe', 'jane@example.com');

**3. 다수의 레코드 한 번에 추가**
여러 개의 레코드를 한 번에 추가할 수 있습니다.

INSERT INTO users (username, email, age) VALUES
    ('alice', 'alice@example.com', 30),
    ('bob', 'bob@example.com', 28),
    ('charlie', 'charlie@example.com', 35);

**4. 컬럼의 일부만 선택하여 추가**
특정 컬럼만 선택하여 값을 추가할 수 있습니다.

INSERT INTO users (username, email) VALUES
    ('david', 'david@example.com'),
    ('elena', 'elena@example.com');


**5. 중복된 레코드 피하기**
중복된 값이 있는 경우 레코드를 추가하지 않고 에러를 방지합니다.

INSERT IGNORE INTO users (username, email, age) VALUES ('john_doe', 'john@example.com', 25);


**6. 중복된 레코드 업데이트**
중복된 값이 있는 경우 해당 레코드를 업데이트합니다.

INSERT INTO users (username, email, age) VALUES ('john_doe', 'john@example.com', 25)
ON DUPLICATE KEY UPDATE age = 25;


**7. AUTO_INCREMENT 컬럼 다루기**
AUTO_INCREMENT를 가진 컬럼은 자동으로 증가하는 값을 가지며, 명시적으로 값을 지정하지 않습니다.

INSERT INTO users (username, email) VALUES ('frank', 'frank@example.com');

이러한 INSERT 쿼리문을 적절히 활용하여 데이터를 효과적으로 데이터베이스에 추가할 수 있습니다.

**8. VALUES 또는 SET을 사용하여 여러 레코드를 동시에 삽입**
한 번의 INSERT 문에서 여러 개의 VALUES 또는 SET 절을 사용하여 여러 레코드를 동시에 삽입할 수 있습니다.

INSERT INTO users (username, email, age)
VALUES ('john', 'john@example.com', 25),
       ('jane', 'jane@example.com', 28),
       ('bob', 'bob@example.com', 30);

**9. SET 문을 사용한 추가**
SET을 사용하여 컬럼에 여러 값들을 설정할 수 있습니다.

INSERT INTO users SET username='john', email='john@example.com', age=25;


### 데이터 조회 - SELECT FROM

**(1) 기본적인 조회 - SELECT**
-- 모든 컬럼 조회
SELECT * FROM users;

-- 특정 컬럼만 조회
SELECT user_id, username, email FROM users;


**(2) 중복 데이터 삭제 - DISTINCT**
-- 중복 제거한 나이 조회
SELECT DISTINCT age FROM users;

**(3) 일시적으로 추가 컬럼 만들기 - AS**
-- 나이와 나이에 100을 곱한 값을 조회
SELECT age, age * 100 FROM users;

-- AS를 사용하여 새로운 컬럼명 정의
SELECT age, age * 100 AS age100 FROM users;


**(4) 데이터 정렬하기 - ORDER BY**
-- 나이순으로 오름차순 정렬
SELECT * FROM users ORDER BY age;

-- 나이순으로 내림차순 정렬
SELECT * FROM users ORDER BY age DESC;

-- 여러 기준으로 정렬 (ASC: 오름차순, DESC: 내림차순)
SELECT * FROM users ORDER BY age ASC, created DESC;

**(5) 조건문 - WHERE**
-- 특정 조건에 맞는 데이터 조회
SELECT * FROM users WHERE age = 30;

-- 특정 조건 이상 데이터 조회
SELECT * FROM users WHERE age >= 30;

-- AND, OR를 사용한 복합 조건
SELECT * FROM users WHERE age = 33 AND name = 'Leo';
SELECT * FROM users WHERE age = 33 OR name = 'Leo';

-- NOT을 사용한 부정 조건
SELECT * FROM users WHERE NOT age = 33;

-- BETWEEN을 사용한 범위 지정
SELECT * FROM users WHERE age BETWEEN 20 AND 25;


**(6) 특정 개수 제한 - LIMIT**
-- 상위 5개의 데이터 조회
SELECT * FROM users LIMIT 5;

-- 10번째부터 5개의 데이터 조회 (페이징)
SELECT * FROM users LIMIT 10, 5;

**(7) 결과 그룹핑 - GROUP BY**
-- 나이별로 그룹화하여 그룹별 데이터 개수 조회
SELECT age, COUNT(*) as user_count FROM users GROUP BY age;

**(8) 특정 조건에 따라 값 변환 - CASE WHEN**
-- 나이가 30 이상인 경우 '성인', 미만인 경우 '미성년자'로 변환하여 조회
SELECT
  name,
  age,
  CASE WHEN age >= 30 THEN '성인' ELSE '미성년자' END AS age_group
FROM users;


**(9) 여러 테이블 조인 - JOIN**
-- users 테이블과 orders 테이블을 user_id를 기준으로 조인
SELECT users.name, users.age, orders.order_id
FROM users
JOIN orders ON users.user_id = orders.user_id;

**(10) 결과 내림차순으로 순위 부여 - ROW_NUMBER()**
-- 나이에 따라 내림차순으로 순위 부여하여 조회
SELECT
  name,
  age,
  ROW_NUMBER() OVER (ORDER BY age DESC) AS rank
FROM users;

### 데이터 업데이트 - UPDATE SET
## **기본적인 `UPDATE` 쿼리**
UPDATE 테이블명
SET 컬럼1 = 값1, 컬럼2 = 값2, ...
WHERE 조건:
- **테이블명**: 업데이트할 테이블의 이름
- **컬럼 = 값**: 업데이트할 컬럼과 새로운 값을 지정
- **WHERE 조건**: 어떤 레코드를 업데이트할지 결정하는 조건

**`UPDATE` 쿼리**
-- users 테이블에서 id가 1인 레코드의 이름을 'John'으로 수정
UPDATE users
SET name = 'John'
WHERE id = 1;

**여러 레코드 동시에 업데이트**
-- age가 25 이상인 모든 레코드의 salary를 50000으로 수정
UPDATE users
SET username = 'senior'
WHERE age >= 60;

- `SET SQL_SAFE_UPDATES = 0;` (세이프 모드 비활성화)
**업데이트된 레코드 수 확인**
-- 업데이트된 레코드 수 반환
SELECT ROW_COUNT();

**`CASE` 문을 사용한 업데이트**
-- user의 age가 60 이상인 경우 'senior'로 username 설정, 
-- 그 외의 경우 username은 'young'로 설정

UPDATE users
SET username = CASE
    WHEN age >= 60 THEN 'senior'
    ELSE 'young'
END;

**`LIMIT`을 사용한 일부 레코드만 업데이트**
-- age가 30인 레코드 중에서 가장 나이가 어린 5명의 salary를 60000으로 수정
UPDATE users
SET username = 'top5_young_people'
WHERE age = 30
LIMIT 5;

**`SUBQUERY`를 사용한 업데이트**
-- 다른 서브쿼리 결과에 따라 업데이트
UPDATE products
SET price = price * 1.1
WHERE category_id IN (SELECT id FROM categories WHERE name = 'Electronics');

**`REGEXP`를 사용한 업데이트**
-- 정규 표현식을 활용하여 업데이트
UPDATE users
SET email = CONCAT(email, '_new')
WHERE email REGEXP '@example\.com$';

**`CASE` 문을 사용한 다양한 조건에 따른 업데이트**
-- 다양한 조건에 따라 다른 업데이트 수행
UPDATE products
SET price = CASE
    WHEN stock < 10 THEN price * 1.1
    WHEN stock >= 10 AND stock < 50 THEN price * 1.05
    ELSE price
END;

### 데이터 제거 - DELETE FROM
**기본적인 삭제**
-- 특정 테이블에서 모든 행 삭제
DELETE FROM users;

**조건을 사용한 삭제**
-- 특정 조건을 만족하는 행 삭제
DELETE FROM users WHERE age < 18;

**`LIMIT`을 사용한 삭제**
-- 특정 개수 이상의 행을 삭제하지 않도록 제한
DELETE FROM orders WHERE status = 'canceled' LIMIT 100;

**`JOIN`을 사용한 삭제**
-- 다른 테이블과 조인하여 삭제
DELETE e FROM employees AS e
JOIN departments AS d ON e.department_id = d.id
WHERE d.name = 'Marketing';


**`USING`을 사용한 삭제**
-- 다른 테이블과 조인하여 삭제 (USING 구문 활용)
DELETE FROM employees
USING employees, departments
WHERE employees.department_id = departments.id AND departments.name = 'HR';

**`RETURNING`을 사용한 삭제 및 반환**

-- 삭제한 행 반환 (PostgreSQL에서 사용 가능)
DELETE FROM users WHERE age > 65 RETURNING *;

### **테이블 생성**
users 테이블
CREATE TABLE users (
    user_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    username TEXT NOT NULL,
    email TEXT NOT NULL
);

orders 테이블
CREATE TABLE orders (
    order_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT,
    product_name VARCHAR(255),
    quantity INT,
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);
### 파이썬으로 **데이터 랜덤 생성(generate)**
설치가 필요한 패키지
bash
pip install mysql-connector-python faker


**app.py**
import mysql.connector
from faker import Faker
import random # 파이썬 기본 모듈

# (1) MYSQL 연결 설정
db_connection = mysql.connector.connect(
    host='localhost',
    user='root',
    password='oz-password',
    database='testdatabase'
)

# (2) MYSQL 연결
cursor = db_connection.cursor()
faker = Faker()

# 100명의 users 더미 데이터 생성
for _ in range(100):
    username = faker.user_name()
    email = faker.email()

    sql = "INSERT INTO users(username, email) VALUES(%s, %s)"
    values = (username, email)

    cursor.execute(sql, values)
    
# user_id 불러오기
cursor.execute("SELECT user_id FROM users")
valid_user_id = [row[0] for row in cursor.fetchall()]

# 100개의 주문 더미 데이터 생성
for _ in range(100):
    user_id = random.choice(valid_user_id)
    product_name = faker.word()
    quantity = random.randint(1, 10)

    try:
        sql = "INSERT INTO orders(user_id, product_name, quantity) VALUES(%s, %s, %s)"
        values = (user_id, product_name, quantity)

        cursor.execute(sql, values)
    except:
        print("오류 발생")
        pass

db_connection.commit()
cursor.close()
db_connection.close()


### 데이터 조인 - INNER, LEFT, RIGHT, FULL JOIN
- 두 개 이상의 테이블을 연결하여 하나의 테이블처럼 출력하고 싶을 때 사용

1. **INNER JOIN (내부 조인):**
    테이블 A를 기준으로 테이블 B를 합하여 생성

    (기본구조)
    SELECT * FROM TABLE A
    LEFT JOIN TABLE B 
    ON A.key = B.key
    
    
    모든 사용자와 그들이 만든 주문을 조회합니다. 사용자와 주문 테이블 간의 **`user_id`**를 기준으로 매칭된 행을 반환합니다.
    
    SELECT * FROM users
    INNER JOIN orders ON users.user_id = orders.user_id;
    
2. **LEFT JOIN (왼쪽 조인):**
    사용자 테이블의 모든 행을 포함하고, 주문 테이블과 매칭되는 경우 해당 주문 정보를 포함합니다.
    
    SELECT * FROM users
    LEFT JOIN orders ON users.user_id = orders.user_id;
    

3. **RIGHT JOIN (오른쪽 조인):**
    주문 테이블의 모든 행을 포함하고, 사용자 테이블과 매칭되는 경우 해당 사용자 정보를 포함합니다.

    SELECT * FROM users
    RIGHT JOIN orders ON users.user_id = orders.user_id;

1. **테이블의 데이터만 삭제 - TRUNCATE**

    TRUNCATE TABLE users;