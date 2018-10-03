---
title: "SQL Database 정리(~ SQL Dates) "
layout: post
date: 2018-10-04 02:27
category: blog
author: Yonghee
---
## w3school SQL Database
https://www.w3schools.com/ 사이트에 sql `데이터베이스 내용(~ SQL Dates)`을 번역하여 정리한 내용입니다.

-------

### SQL CREATE DATABASE 구문
CREATE DATABASE 구문은 새로운 SQL 데이터 베이스를 생성할 때 사용한다.

> CREATE DATABASE Syntax

```
CREATE DATABASE databasename;
```

##### EXAMPLE

```
CREATE DATABASE testDB;
```

```
TIP: 새로운 데이터 베이스를 만들기 전에 관리자 권한이 있어야 한다.
데이터 베이스가 생성되면 다음 SQL 명령을 사용해 데이터 베이스 목록에서 데이터 베이스를 확인할 수 있다.

SHOW DATABASESE;
```

### SQL DROP DATABASE 구문
DROP DATABASE 구문은 기존 SQL 데이터 베이스를 삭제할 때 사용한다.
> DROP DATABASE Syntax

```
DROP DATABASE databasename;
```

`Note: 데이터 베이스를 제거하기 전에 주의하자!`

`데이터 베이스를 삭제하면 데이터 베이스에 저장된 내용은 모두 삭제된다.`

##### EXAMPLE
```
DROP DATABASE testDB;
```

```
TIP: 데이터 베이스를 삭제하기 전에 관리자 권한이 있어야 한다.
데이터 베이스가 삭제되면 다음 SQL 명령을 사용해 데이터 베이스 목록에서
데이터 베이스를 확인할 수 있다.

SHOW DATABASESE;
```

### SQL CREATE TABLE 구문
CREATE TABLE 구문은 데이터 베이스 안에 새로운 테이블을 만들 때 사용한다.
> SQL CREATE TABLE Syntax

```
CREATE TABLE table_name(
	column1 datatype,
	column2 datatype,
	column3 datatype,
	...
);
```
`column` 매개 변수는 테이블의 `column` 이름을 지정한다.

`datatype` 매개 변수는 `column` 에서 보유할 수 있는 데이터 유형(varchar, integer, date, etc.)을 지정한다.

** TIP: 사용 가능한 데이터 유형에 대한 개요는 DATA TYPE REFERENCE 를 이동해라. **

##### EXAMPLE

```
CREATE TABLE Persons(
	PersonID int,
	LastName varchar(255),
	FirstName varchar(255),
	Address varchar(255),
	City varchar(255)
);
```
### 다른 테이블을 이용해 테이블 만들기
기존에 있는 테이블을 CREATE TABLE 과 SELECT 구문의 조합으로 새로운 테이블 만들 수 있다.

새 테이블은 동일안 coulumn 의 정의를 갖고온다. 모든 column 과 특정 column을 선택할 수 있다.

기존 테이블을 사용해 새 테이블을 만들려면, 새 테이블은 기존 테이블 안에 존재하는 값으로 채워진다.

> CREATE TABLE Syntax

```
CREATE TABLE new_table_name AS
	SELECT column1, column2, ...
	FROM existing_table_name
	WHERE condition;
```

### SQL DROP TABLE 구문

DROP TABLE 구문은 데이터 베이스 안에 있는 테이블을 삭제할 때 사용한다.
> DROP TABLE Syntax

```
DROP TABLE table_name;
```

`Note: 테이블을 삭제하기 전에 주의하자! 테이블을 삭제하면 테이블에 저장된 정보가 완전히 삭제된다.`

##### EXAMPLE
```
DROP TABLE Shippers;
```

### SQL TRUNCATE TABLE
TRUNCATE TABLE 구문은 테이블 내부의 데이터는 삭제하지만 테이블 자체를 삭제하지 않는다.
> TRUNCATE TABLE Syntax

```
TRUNCATE TABLE table_name;
```

### SQL ALTER TABLE 구문
`ALTER TABLE` 구문은 기존 테이블 안 `column` 을 더하거나 삭제, 수정할 때 사용한다.

`ALTER TABLE` 구문은 기존 테이블에 다양한 제한 조건을 추가하고 삭제할 때 사용한다.

> ALTER TABLE - ADD

```
ALTER TABLE table_name
ADD column_name datatype;
```

> ALTER TABLE - DROP COLUMN

```
ALTER TABLE table_name
DROP COLUMN column_name;
```

> ALTER TABLE - ALTER / MODIFY COLUMN

```
<!-- SQL Server / MS Access -->
ALTER TABLE table_name
ALTER COLUMN column_name datatype;

<!-- MySQL / Oracle(prior version 10G) -->
ALTER TABLE table_name
MODIFY COLUMN column_name datatype;

<!-- Oracle 10G and later -->
ALTER TABLE table_name
MODIFY column_name datatype;
```

### SQL CREATE CONSTRAINTS
CREATE TABLE 또는 ALTER TABLE 구문으로 테이블을 생성하고 난 후 제한조건을 지정할 수 있다.

> Constraints Syntax

```
CREATE TABLE talbe_name (
	column1 datatype CONSTRAINTS,
	column2 datatype CONSTRAINTS,
	column3 datatype CONSTRAINTS,
	...
);
```

### SQL 제약조건

- SQL 제약조건은 테이블 안 데이터에 대해 규칙을 지정할 때 사용한다.

- 제약조건은 테이블 안에 들어 갈 수 있는 데이터 유형을 제한할 때 사용한다.

- 제약조건을 할 경우 테이블 안 데이터의 정확성과 신뢰성이 보장된다.

- 제한 조건과 데이터 사이에 위반이 있을 경우, 작동이 중지된다.

- 제약조건은 `column` 또는 테이블 레벨일 수 있다. `column` 레벨 제한조건은 `column` 에 적용되고, 테이블 레벨 제한조건은 테이블 전체에 적용된다.

- SQL 에는 다음과 같은 제약조건이 있다.
  - NOT NULL: `column` 이 `NULL` 값을 갖지 못한다.
  - UNIQUE: `column` 안 모든 값이 서로 다른 지 확인한다.
  - PRIMARY KEY: `NOT NULL` 과 `UNIQUE` 의 조합으로 테이블의 각 `row` 를 고유하게 식별한다.
  - FOREIGN KEY: 다른 테이블의 `row/`레코드를 고유하게 식별한다.
  - CHECK: `column` 의 모든 값이 특정 조건을 충족하는지 확인한다.
  - DEFAULT: 값이 지정되지 않은 경우, `column` 에 기본값을 설정한다.
  - INDEX: 데이터 베이스에서 데이터를 매우 신속하게 생성하고 검색할 때 사용한다.

### SQL NOT NULL 제약조건

기본적으로 `NULL` 값은 `column` 에 포함할 수 있다.

`NOT NULL` 제약조건은 `column` 이 `NULL` 값을 허용하지 않도록 강제한다.

`NOT NULL` 을 사용할 경우 필드에 값이 항상 존재하도록 강제한다.

** 즉, 새 레코드를 삽입하거나 업데이트 할 때 필드에 값을 추가하지 않으면 안된다. **

`TIP: 기존 테이블이 있는 경우, ALTER TABLE 구문을 통해 제약조건을 NOT NULL 로 추가할 수 있다.`

##### EXAMPLE
```
CREATE TABLE Persons(
	ID int NOT NULL,
	LastName varchar(255) NOT NULL,
	FristName varchar(255) NOT NULL,
	Age int
);
```

### SQL UNIQUE 제약조건
`UNIQUE` 제약조건은 `column` 의 모든 값이 다른 지 확인한다.

`UNIQUE` 및 `PRIMARY KEY` 제약조건은 `column` 또는 `column`집합의 고유성을 보장한다.

`PRIMARY KEY` 제약조건은 자동으로 `UNIQUE` 제약조건이 있다.

** 그러나 테이블 당 많은 `UNIQUE` 제약조건을 갖을 수 있지만, `PRIMARY KEY` 제약조건은 테이블 당 하나만 존재한다. **

### CREATE TABLE 에서 SQL UNIQUE 제약조건
```
<!-- SQL Server / Oracle / MS Access -->
CREATE TABLE Persons(
	ID int NOT NULL UNIQUE,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255) NOT NULL,
	Age int
);

<!-- MySQL -->
CREATE TABLE Persons(
	ID int NOT NULL,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255) NOT NULL,
	Age int,
	UNIQUE(ID)
);

<!-- MySQL / SQL Server / Oracle / MS Access -->
CREATE TABLE Persons(
	ID int NOT NULL,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255) NOT NULL,
	Age int,
	CONSTRAINT UC_Person UNIQUE(ID, LastName)
);
```

### ALTER TABLE 에서 SQL UNIQUE 제약조건
기존 테이블이 있는 경우, `ALTER TABLE` 구문을 통해 `UNIQUE` 제약조건을 생성한다.
```
<!-- MySQL / SQL Server / Oracle / MS Access -->
 ALTER TABLE Persons
 ADD UNIQUE(ID);

 ALTER TABLE Persons
 ADD CONSTRAINT UC_Person UNIQUE(ID, LastName);

<!-- MySQL -->
 ALTER TABLE Persons
 DROP INDEX UC_Person;

<!-- SQL Server / Oracle / MS Access -->
ALTER TABLE Persons
DROP CONSTRAINT UC_Person;
```

### SQL PRIMARY KEY 제약조건
`PRIMARY KEY` 제약조건은 데이터 베이스 안 각 레코드를 고유하게 식별한다.

`PRIMARY KEY` 는 고유한 값을 갖으며, `NULL` 값을 갖을 수 없다.

테이블에서 오직 하나의 `PRIMARY KEY` 만 있을 수 있으며, 하나 또는 여러 개의 필드로 구성 될 수 있다.

### CREATE TABLE에서 SQL PRIMARY KEY 생성
```
<!-- MySQL -->
CREATE TABLE Persons(
	ID int NOT NULL,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255) NOT NULL,
	Age int,
	PRIMARY KEY(ID)
);

<!-- SQL Server / Oracle / MS Access -->
CREATE TABLE Persons(
	ID int NOT NULL PRIMARY KEY,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255) NOT NULL,
	Age int
);
```
`PRIMARY KEY` 제약조건에 이름을 지정하고 여러 `column` 에 대해 `PRIMARY KEY` 제약조건을 지정할 경우 다음과 같이 정의한다.

```
<!-- MySQL / SQL Server / Oracle / MS Access -->
CREATE TABLE Persons(
  ID int NOT NULL,
  LastName varchar(255) NOT NULL,
  FirstName varchar(255) NOT NULL,
  Age int,
  CONSTRAINT PK_Person PRIMARY KEY(ID, LastName)
);
```
`Note: 위에서는 두 개의 PRIMARY KEY 가 존재하는 것이 아니라`

`ID, LastName 두 column 이 하나로 묶여 하나의 PRIMARY KEY 로 구성되어 있다.`

### ALTER TABLE 을 이용한 PRIMARY KEY
기존 테이블이 있는 경우 `ALTER TABLE` 구문을 통해 `PRIMARY KEY` 제약조건을 생성할 수 있다.
```
<!-- MySQL / SQL Server / Oracle / MS Access -->
ALTER TABLE Persons
ADD PRIMARY KEY(ID);

ALTER TABLE Person
ADD CONSTRAINT PK_Person PRIMARY KEY(ID, LastName);

ALTER TABLE Persons
DROP PRIMARY KEY;

ALTER TABLE Persons
DROP CONSTRAINT PK_Person;
```
`ALTER TABLE` 구문을 사용해 `PRIMARY KEY` 를 추가하는 경우, 해당 `column` 은 `NOT NULL` 제약조건이 있어야 한다.

### SQL FOREIGN KEY 제약조건
`FOREIGN KEY` 는 두 테이블을 연결할 때 사용되는 키이다.

`FOREIGN KEY` 는 다른 테이블의 `PRIMARY KEY` 를 참조하는 테이블의 필드(또는 필드 모음)이다.

`FOREIGN KEY` 가 있는 테이블을 자식 테이블, `CANDIDATE KEY` 가 있는 테이블을 참조 테이블 또는 부모 테이블이라 부른다.

### CREATE TABLE 에서 SQL FOREIGN KEY
```
<!-- MySQL -->
CREATE TABLE Orders(
	OrderID int NOT NULL,
	OrderNumber int NOT NULL,
	PersonID int,
	PRIMARY KEY(OrderID),
	FOREIGN KEY(PersonID) REFERENCES Persons(PersonID)
);

<!-- SQL Server / Oracle / MS Access -->
CREATE TABLE Orders(
	OrderID int NOT NULL PRIMARY KEY,
	OrderNumber int NOT NULL,
	PersonID int,
	PRIMARY KEY(OrderID) FOREIGN KEY REFERENCES Persons(PersonID)
);

<!-- MySQL / SQL Server / Oracle / MS Access -->
CREATE TABLE Orders(
	OrderID int NOT NULL,
	OrderNumber int NOT NULL,
	PersonID int,
	PRIMARY KEY(OrderID),
	CONSTRAINT FK_PersonOrder FOREIGN KEY(PersonID)
	REFERENCES Persons(PersonID)
);
```
### ALTER TABLE 에서 FOREIGN KEY
```
<!-- MySQL -->
ALTER TABLE Orders
ADD FOREIGN KEY(PersonID) REFERENCES Persons(PersonID);

<!-- MySQL / SQL Server / Oracle / MS Access -->
ALTER TABLE Orders
ADD CONSTRAINT FK_PersonOrder
FOREIGN KEY(PersonID) REFERENCES Persons(PersonID)

<!-- MySQL -->
ALTER TABLE Orders
DROP FOREIGN KEY FK_PersonOrder;

<!-- SQL Server / Oracle / MS Access -->
ALTER TABLE Orders
DROP CONSTRAINT FK_PersonOrder;
```

### SQL CHECK 제약조건
`CHECK` 제약조건은 `column` 에 배치할 수 있는 값 범위를 제한할 때 사용한다.

단일 `column` 에 `CHECK` 제약조건을 정의하면 `column` 에 대해 특정 값만 허용된다.

테이블에 `CHECK` 제약조건을 정의하면 `row` 의 다른 `column` 에 있는 값을 기반으로 특정 `column` 값을 제한할 수 있다.

### CREATE TABLE 에서 CHECK 제약조건
```
<!-- MySQL -->
CREATE TABLE Persons(
	ID int NOT NULL,
	LastName varchar(255) NOT NULL,
	FristName varchar(255),
	Age int,
	CHECK(Age>=18)
);

<!-- SQL Server / Oracle / MS Access -->
CREATE TABLE Persons(
	ID int NOT NULL,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255),
	Age int CHECK(Age>=18)
);

<!-- MySql / SQL Server / Oracle / MS Access -->
CREATE TABLE Persons(
	ID int NOT NULL,
	LastName vachar(255) NOT NULL,
	FirstName varchar(255),
	Age int,
	City varchar(255),
	CONSTRAINT CHK_Person CHECK(Age>=18 AND City='Sandnes')
);
```

### ALTER TABLE 에서 SQL CHECK
```
<!-- MySQL / SQL Server / Oracle / MS Access -->
ALTER TABLE Persons
ADD CHECK(Age>=18);

ALTER TABLE Persons
ADD CONSTRAINT CHK_Person CHECK(Age>=18 AND City='Sandnes');

<!-- MySQL -->
ALTER TABLE Persons
DROP CHECK CHK_Person;

<!-- SQL Server / Oracle / MS Access -->
ALTER TABLE Persons
DROP CONSTRAINT CHK_Person;
```

### SQL DEFAULT 제약조건
`DEFAULT` 제약조건은 `column` 의 기본값을 제공할 때 사용한다.

다른 값을 지정하지 않으면, 기본 값이 새로운 레코드에 추가된다.

### CREATE TABLE 에서 DEFAULT 제약조건
```
<!-- MySQL / SQL Server / Oracle / MS Access -->
CREATE TABLE Persons(
	ID int NOT NULL,
	LastName varchar(255) NOT NULL,
	FristName varchar(255),
	Age int,
	City varchar(255) DEFAULT 'Sandnes'
);

CREATE TABLE Orders(
	ID int NOT NULL,
	OrderNumber int NOT NULL,
	OrderDate date DEFAULT GETDATE()
);
```

### ALTER TABLE 에서 DEFAULT 제약조건
```
<!-- MySQL -->
ALTER TABLE Persons
ALTER City SET DEFAULT 'Sandnes';

<!-- SQL Server / MS Access -->
ALTER TABLE Persons
ALTER COLUMN City SET DEFAULT 'Sandnes';

<!-- Oracle -->
ALTER TABLE Persons
MODIFY City DEFAULT 'Sandnes';

<!-- MySQL -->
ALTER TABLE Persons
ALTER City DROP DEFAULT;

<!-- SQL Server / Oracle / MS Access -->
ALTER TABLE Persons
ALTER COLUMN City DROP DEFAULT;
```

### SQL CREATE INDEX 구문
`CREATE INDEX` 구문은 테이블에 인덱스를 만들 때 사용한다.

인덱스는 데이터 베이스에서 데이터를 매우 빠르게 검색할 때 사용하며, 사용자는 색인을 볼 수 없다. 검색/쿼리 속도를 높이기 위해 사용한다.

`Note: 인덱스 없이 테이블을 업데이트하는 것보다 인덱스를 사용해 테이블을 업데이트 하는 것이 시간이 더 걸린다(인덱스도 업데이트가 필요하기 때문!). 따라서 자주 검색할 column 에 대해서만 인덱스를 작성해라.`

### CREATE/DROP INDEX Syntax
```
CREATE INDEX index_name
ON table_name(column1, column2, ...);

<!-- 중복된 값을 허용하지 않는 인덱스 -->
CREATE UNIQUE INDEX index_name
ON table_name(column1, column2, ...);

<!-- MS Access -->
DROP INDEX index_name ON table_name;

<!-- SQL Server -->
DROP INDEX table_name.index_name;

<!-- DB2 / Oracle -->
DROP INDEX index_name;

<!-- MySQL -->
ALTER TABLE table_name
DROP INDEX index_name;
```
`Note: 인덱스를 만드는 구문은 데이터 베이스 마다 다르다. 꼭 데이터 베이스의 인덱스 작성 구문을 확인해라.`

##### EXAMPLE
```
CREATE INDEX idx_lastname
ON Persons(LastName);

CREATE INDEX idx_pname
ON Persons(LastName, FirstName);
```
### SQL AUTO INCREMENT 필드
`AUTO INCREMENT` 는 테이블에 새로운 레코드가 삽입될 때 고유번호가 자동적으로 생성하게 한다.

새로운 레코드가 삽입될 때마다, `AUTO INCREMENT`는 자동적으로 `PRIMARY KEY` 필드에 생성되길 원할 때 자주 쓰인다.

### AUTO INCREMENT Syntax
```
<!-- MySQL -->
CREATE TABLE Persons(
	ID int NOT NULL AUTO_INCREMENT,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255),
	Age int,
	PRIMARY KEY(ID)
);

<!-- ID 의 시작 값이 100부터 시작된다. -->
ALTER TABLE Persons AUTO_INCREMENT=100;

<!-- SQL Server -->
CREATE TABLE Persons(
	ID int IDENTITY(1,1) PRIMARY KEY,
	# ID int IDENTITY(10, 5) PRIMARY KEY, <-- 이 경우 ID 값이 10에서 시작해서 5씩 증가된다.
	LastName varchar(255) NOT NULL,
	FirstName varchar(255),
	Age int
);

<!-- MS Access -->
CREATE TABLE Persons(
	ID Integer PRIMARY KEY AUTOINCREMENT,
	# ID Integer PRIMARY KEY AUTOINCREMENT(10, 5) <-- 이 경우 ID 값이 10에서 시작해서 5씩 증가한다.
	LastName varchar(255) NOT NULL,
	FirstName varchar(255),
	Age int
);

INSERT INTO Persons(FirstName, LastName)
VALUES('Lars', 'Monsen');

<!-- Oracle -->
CREATE SEQUENCE seq_person
MINVALUE 1
START WITH 1
INCREMENT BY 1
CACHE 10;

INSERT INTO Persons(ID, FirstName, LastName)
VALUES(seq_person.nextval, 'Lars', 'Monsen');
```
`MySQL` 은 `AUTO_INCREMENT` 키워드를 사용해 자동증가 기능을 수행한다.

기본적으로 `AUTO_INCREMENT` 의 시작 값은 `1`이며, 새로운 레코드가 삽입될 때 `1씩 증가`한다.

`Oracle` 은 코드가 까다롭다.

`SEQUENCE` 객체를 자동증가 필드를 생성한다(이 객체는 숫자 시퀀스를 생성한다).

새로운 레코드에 `ID` 값을 삽입할 때 `nextval` 함수를 사용한다.
