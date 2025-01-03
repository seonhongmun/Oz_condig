# 02. RDBMS

## RDBMS(Relational DBMS)란?
RDBMS(관계형 데이터베이스 관리 시스템)는 표 형태로 데이터를 구조화하고 관리하는 데이터베이스
관계형 데이터베이스는 데이터를 테이블 형태로 구조화하는 방식입니다. 
이는 2차원 테이블을 사용하여 데이터를 정의하고 표현하는 데이터 모델입니다. 여기서 데이터는 속성(Attribute)과 해당 속성에 대응하는 데이터 값(Attribute Value)으로 이뤄져 있습니다.
구체적으로 말하면, 데이터를 정리하고 설명하기 위해 속성과 데이터 값 간의 관계를 찾아내어 이를 테이블 형태로 나타냅니다. 이 테이블은 열(Column)과 행(Row)으로 이뤄져 있으며, 각 열은 데이터의 속성을 나타내고 각 행은 해당 속성에 대응하는 데이터 값을 포함하고 있습니다.

## RDBMS 기본 구조(Structure)
- Column = Attribute = Field (컬럼)
- Row = Record = Tuple (행)
Database → Table → Column, Row

1. **스키마(Schema)**: 데이터베이스의 구조를 정의하는 것입니다. 스키마는 테이블, 행, 열, 인덱스, 관계 등의 데이터베이스 구조를 명시합니다.
2. **SQL(Structured Query Language)**: 데이터베이스에서 데이터를 관리하기 위해 사용되는 표준 프로그래밍 언어입니다. SQL을 사용하여 데이터베이스에 질의, 업데이트, 삭제 등의 작업을 수행할 수 있습니다.
3. **인덱스(Index)**: 데이터베이스에서 데이터 검색 속도를 빠르게 하기 위해 사용되는 객체입니다. 인덱스는 특정 열에 대한 포인터를 포함하여 데이터 검색 시간을 단축시킵니다.
4. **데이터베이스 관리 시스템(DBMS)**: 데이터베이스를 생성하고 관리하는 소프트웨어입니다. 예를 들어, MySQL, PostgreSQL, Oracle, Microsoft SQL Server 등이 있습니다.
5. **트랜잭션(Transaction)**: 데이터베이스의 상태를 변화시키는 하나의 작업 단위입니다. 트랜잭션은 데이터 무결성을 유지하는 데 중요한 역할을 합니다.

**단점:**
1. **성능:** 대용량 데이터 처리나 복잡한 쿼리에 대한 성능이 다른 모델에 비해 낮을 수 있습니다.
2. **확장 어려움:** 수직적 확장이 한계가 있고, 수평적 확장은 복잡하고 비용이 많이 들 수 있습니다.
3. **유연성 부족:** 스키마 변경이 어려워서 요구사항 변경에 대응하기 어려울 수 있습니다.
4. **복잡한 조인:** 많은 테이블 간의 조인은 성능에 부정적인 영향을 미칠 수 있습니다.
5. **고비용:** 서버 하드웨어 및 라이선스 비용이 상대적으로 높을 수 있습니다.

RDBMS는 데이터의 구조화와 안정성 측면에서 강력하며, 일반적인 업무 응용에 적합합니다. 그러나 성능이나 유연성 등의 측면에서 고려해야 할 부분도 있습니다.

## **RDBMS의 구성 요소**
1. 데이터 베이스 (학교)
2. 테이블=모델 (학생, 교실, 선생님(급여), 행사, 급식, 동아리, 방과후활동, 과목, 시험, 비품)
3. 행 : 하나의 데이터
4. 열 : 컬럼
    1. (테이블) 학생 - (컬럼) 나이, 성별, 주소, 성적
    2. 교실 - 학생수, 평균성적 
    3. 선생님 - 나이, 성별, 주소, 급여
5. 키 : ID
    1. PK (Primary Key) id or pk
        1. 테이블 내에서 중복이 절대 불가능 (고유값으로 사용이 가능)
        2. 행(=하나의 데이터)을 식별할 수 있는 유일한 값
        3. 유니크한 값이면 가능
            1. 주민등록번호
            2. 국가 코드 (+82, +1, +86 …)
            3. 학번 (2010+119+09)
            4. 군번
    2. FK (Foreign Key)
        1. 다른 테이블의 기본키로 지정된 키
    
    1. **데이터베이스(Database)**: 구조화된 데이터의 집합입니다. 데이터베이스는 데이터를 저장, 검색, 수정, 삭제할 수 있게 해주는 시스템입니다.
    2. **테이블(Table)**: 데이터베이스 내에서 데이터가 저장되는 장소입니다. 테이블은 행(Row)과 열(Column)의 격자 형태로 구성됩니다.
    3. **행(Row)/레코드(Record)**: 테이블 내의 개별 데이터 항목을 나타냅니다. 각 행은 하나의 데이터 항목 또는 개체를 나타냅니다.
    4. **열(Column)/필드(Field)**: 테이블 내의 특정 카테고리 또는 데이터 유형을 나타냅니다.
    
    1. **기본 키(Primary Key)**: 테이블 내의 각 행을 고유하게 식별하는 열입니다. 기본 키 값은 유일해야 하며, 각 행마다 다른 값을 가져야 합니다.
    2. **외래 키(Foreign Key)**: 다른 테이블의 기본 키를 참조하는 열입니다. 외래 키는 두 테이블 간의 관계를 설정하는 데 사용됩니다.
    

## **대표적인 RDBMS**
1. **MySQL:**
    - 개방 소스 RDBMS로서 가장 인기 있는 데이터베이스 중 하나입니다. 다양한 환경에서 사용되며, 웹 애플리케이션부터 대규모 엔터프라이즈 시스템에 이르기까지 다양한 용도로 활용됩니다.
2. **PostgreSQL:**
    - 객체 관계형 데이터베이스 시스템으로, 확장 가능하고 풍부한 기능을 제공합니다. ACID 호환성 및 다양한 데이터 유형을 지원하여 고급 데이터베이스 요구에 적합합니다.
3. **Microsoft SQL Server:**
    - Microsoft에서 제공하는 RDBMS로, Windows 기반 환경에서 주로 사용됩니다. 엔터프라이즈 급 데이터베이스 솔루션으로 개발 및 관리에 용이합니다.
4. **Oracle Database:**
    - 오라클이 개발한 대규모 엔터프라이즈용 RDBMS입니다. 뛰어난 성능과 안정성, 확장성을 제공하여 대부분의 산업 분야에서 사용됩니다.
5. **SQLite:**
    - 경량이면서도 서버 없이 로컬에서 사용할 수 있는 RDBMS입니다. 임베디드 시스템이나 모바일 애플리케이션에서 많이 활용됩니다.
이 중 MySQL과 PostgreSQL는 오픈 소스로 무료로 사용할 수 있어 커뮤니티에서도 널리 사용되고 있습니다. Microsoft SQL Server와 Oracle Database는 주로 기업 환경에서 사용되며, 각각의 특정 용도나 환경에 따라 선택될 수 있습니다. SQLite는 경량 환경이나 모바일 애플리케이션에서 간단한 데이터베이스 요구에 활용됩니다.

## 데이터베이스 스키마(Schema)
데이터베이스 스키마(Schema)는 데이터베이스에서 데이터의 구조와 구성을 정의하는 청사진 또는 설계도입니다. 이는 데이터베이스 테이블, 필드, 관계 등을 어떻게 구성할지를 명세한 것으로, 데이터베이스 시스템이 데이터를 저장, 관리, 조작하는 방식을 결정합니다.
일반적으로 관계형 데이터베이스에서는 여러 테이블로 구성되며, 각 테이블의 속성을 식별하여 컬럼으로 정의합니다.
논리적 스키마:
테이블 간의 관계, 각 테이블의 속성과 데이터 타입, 제약 조건 등

물리적 스키마:
데이터의 실제 저장과 관련이 있는 부분으로, 디스크에 저장하는 방식 등

스키마가 있다면 동일한 구조의 데이터베이스를 쉽게 만들 수 있습니다. 데이터베이스의 백업과는 달리 스키마는 데이터의 구조만을 정의하므로, 데이터 구조를 동일하게 만드는 데 사용됩니다.

## **SQL(Structured Query Language)란?**
SQL(Structured Query Language)은 관계형 데이터베이스에서 데이터를 정의, 처리, 제어하는데 사용되는 표준화된 언어입니다. SQL은 주로 데이터베이스 관리 시스템(DBMS)과의 상호 작용을 위해 설계되었습니다.

### **1. 데이터 정의 언어 (DDL - Data Definition Language)**
DDL은 데이터베이스의 구조를 정의하고 관리하는 데 사용됩니다. 주요 명령어로는 다음이 있습니다:
- **CREATE:** 데이터베이스 객체를 생성합니다. (**`CREATE TABLE`**, **`CREATE INDEX`** 등)
    
    CREATE TABLE employees (
        employee_id INT PRIMARY KEY,
        first_name VARCHAR(50),
        last_name VARCHAR(50),
        hire_date DATE
    );
    
- **ALTER:** 데이터베이스 객체를 수정합니다. (**`ALTER TABLE`** 등)
    
    ALTER TABLE employees
    ADD COLUMN department VARCHAR(50);
    
- **DROP:** 데이터베이스 객체를 삭제합니다. (**`DROP TABLE`** 등)

    DROP TABLE employees;

- **TRUNCATE:** 테이블의 모든 레코드를 삭제하지만 테이블은 유지합니다.
    
    TRUNCATE TABLE employees;
    

### **2. 데이터 처리 언어 (DML - Data Manipulation Language)**
DML은 데이터를 검색, 삽입, 수정, 삭제하는 데 사용됩니다. 주요 명령어로는 다음이 있습니다:

- **SELECT:** 데이터베이스에서 정보를 검색합니다.

    SELECT first_name, last_name FROM employees WHERE department = 'IT';

- **INSERT:** 새로운 데이터를 테이블에 삽입합니다.

    INSERT INTO employees (employee_id, first_name, last_name, hire_date, department)
    VALUES (1, 'John', 'Doe', '2022-01-01', 'IT');

- **UPDATE:** 테이블의 기존 데이터를 수정합니다.

    UPDATE employees SET department = 'HR' WHERE employee_id = 1;

- **DELETE:** 테이블에서 데이터를 삭제합니다.

    DELETE FROM employees WHERE employee_id = 1;


### **3. 데이터 제어 언어 (DCL - Data Control Language)**

DCL은 데이터베이스에 대한 액세스를 제어하는 데 사용됩니다. 주로 다음 명령어가 사용됩니다:
- **GRANT:** 사용자에게 특정 작업을 수행할 권한을 부여합니다.

    GRANT SELECT ON employees TO username;

- **REVOKE:** 사용자로부터 특정 작업 수행 권한을 제거합니다.

    REVOKE SELECT ON employees FROM username;