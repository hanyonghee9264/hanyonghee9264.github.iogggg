---
title: "SQL Tutorial 정리(~ SQL Exists)"
layout: post
date: 2018-10-04 02:27
category: blog
author: Yonghee
---
## w3school SQL Tutorial
https://www.w3schools.com/ 사이트에 sql `튜토리얼 내용(~ SQL Exists)`을 번역하여 정리한 내용입니다.



----
### SQL이란 무엇인가?
- SQL은 Structured Query Language의 줄임말
- 데이터베이스에 접근하고, 조작 가능
- 1986 년에 미국 표준 협회 (ANSI)의 표준이되었고 1987 년에 국제 표준화기구 (ISO)의 표준

### SQL로 무엇을 할 수 있는가?
- SQL은 데이터 베이스에 대해 쿼리를 실행할 수 있다.
- SQL은 데이터 베이스 안 데이터를 검색할 수 있다.
- SQL은 데이터 베이스에 레코드를 삽입할 수 있다.
- SQL은 데이터 베이스 안 레코드를 업데이트 할 수 있다.
- SQL은 데이터 베이스 안 레코드를 삭제할 수 있다.
- SQL은 새로운 데이터 베이스를 생성할 수 있다.
- SQL은 데이터 베이스 안에 저장 프로시저를 생성할 수 있다.
- SQL은 데이터 베이스 안에 뷰를 생성할 수 있다.
- SQL은 테이블, 프로시저, 뷰에 대해 권한을 설정할 수 있다.

### SQL은 표준이지만...
- SQL은 ANSI / ISO 표준이지만 다른 버전의 SQL 언어가 있다.
- 그러나 ANSI 표준을 준수하기 위해 이들은 모두 SELECT, UPDATE, DELETE, INSERT, WHERE와 같은 주요 명령을 비슷한 방식으로 지원한다.

`Note: 대부분의 SQL 데이터 베이스 프로그램은 표준 외의 추가적인 확장 기능을 갖고 있다.`

### 웹 사이트에서 SQL 사용
데이터 베이스의 데이터를 보여주는 웹 사이트를 구축하기 위해서는 아래와 같은 내용이 필요하다.
- RDBMS 데이터베이스 프로그램 (예 : MS Access, SQL Server, MySQL)
- PHP 혹은 ASP 같은 서버 사이드 스크립트 언어를 사용해야 한다.
- SQL 를 사용해야 원하는 데이터를 얻을 수 있다.
- HTML/CSS 를 이용해 웹 페이지에 스타일을 씌운다.

### RDBMS
> 엑셀파일 들을 모아놨다고 생각하자!

- RDBMS(Relational Database Managaement System) 란 `관계형 데이터 베이스 관리 시스템`을 말한다. RDBMS SQL을 비롯한 MS SQL Server, IBM DB2, Oracle, MySQL, Microsoft Access 와 같은 `모든 데이터 베이스 시스템의 기초`가 된다.

- RDBMS 안 데이터는 데이터 베이스 `TABLE` 이라는 `객체`로 저장된다. `TABLE` 은 관련된 데이터 항목의 모음이며 `cloumns (열)`과 `row (행)`으로 이뤄진다. 아래의 ‘Customers’ 테이블을 확인해보자.

  ```python
  SELECT * FROM Customers;
  Result:
  Number of Records: 91

  CustomerID    CustomerName            ContactName    Address            City           PostalCode    Country
  1             Alfreds Futterkiste     Maria Anders   Obere Str. 57      Berlin         12209         Germany
  2             Ana Trujillo Empa..     Ana Trujillo   Avda. de la..      Mexico D.F.    05021         Mexico
  ...more
  ```

- 모든 테이블 은 `필드` 라는 더 작은 엔티티로 나뉜다. **Customers** 테이블의 `필드`는 **CustomerID, CustomerName, ContactName, Address, City, PostalCode, Country** 구성되어 있다. `필드`는 테이블의 모든 레코드에 대한 특정 정보를 유지하고 관리하도록 설계된 `테이블의 열`이다. 열(이 또한 레코드)은 테이블 안에서 `개별적인 항목으로 존재`한다. 위 91개의 레코드를 가진 **Customers** 테이블을 예를 들어보자. `테이블의 수평(가로)` 엔티티는 `레코드`다. `테이블의 수직(세로)` 엔티티인 column열은 테이블의 `특정 필드와 연관된 정보`를 갖고 있다.
---

### SQL Syntax
- `데이터 베이스`는 하나 이상의 `테이블`을 포함한다. 각 테이블은 이름(예: ‘Customers’ or ‘Orders’)으로 확인한다. 그리고 `테이블`은 데이터가 있는 `레코드(row)를 포함`한다.

- 튜토리얼에서는 잘 알려진 Northwind 샘플 데이터베이스를 사용한다.

### 잊지말기!
- `SQL 키워드`는 `대소문자`를 `구분하지 않는다`.
- `select` 와 `SELECT` 는 `같은 것을 의미`한다.
- **W3School 튜토리얼`에서는 모든 SQL 키워드를 대문자로 작성**한다.

### SQL구문 뒤에 오는 세미콜론 (;)
- 몇몇 데이터 베이스 시스템은 SQL `구문이 끝난 후` **세미콜론**을 적어야한다.
- `세미콜론`은 데이터 베이스 시스템에서 **둘 이상의 각각의 SQL 구문을 분리하는 표준방법**이다.
- **w3School 튜토리얼에서는 각 SQL 구문마다 세미콜론을 사용**한다.

### 가장 중요한 SQL 명령 중 일부
- SELECT : 데이터 베이스에서 데이터를 추출한다.
- UPDATE : 데이터 베이스의 데이터를 변경(업데이트)한다.
- DELETE : 데이터 베이스의 데이터를 삭제한다.
- INSERT INTO : 데이터 베이스에 새로운 데이터를 저장(삽입)한다.
- CREATE DATABASE : 새로운 데이터 베이스를 생성한다.
- ALTER DATABASE : 데이터 베이스를 수정한다.
- CREATE TABLE : 새로운 테이블 생성한다.
- ALTER TABLE : 테이블을 수정한다.
- DELETE TABLE : 테이블을 삭제한다.
- CREATE INDEX : 색인(검색 키)를 생성한다.
- DROP INDEX : 색인을 삭제한다.


### SQL SELECT 구문
- SELECT 구문은 데이터 베이스에서 데이터를 선택하는데 사용한다.
- 리턴된 데이터는 RESULT-SET 이라고 하는 결과 테이블에 저장된다.
> SELECT Syntax

  ```python
  SELECT column1, column2, ...
  FROM table_name
  ```
 - 여기에서 column1, column2, …는 데이터를 선택할 테이블의 필드 이름이다.
 - 표에서 사용 가능한 모든 필드를 선택하려면 다음 구문을 사용한다.
 ```python
 SELECT * FROM table_name;
 ```

### SQL SELECT DISTINCT 구문
SELECT DISTINCT 은 고유한 (다른) 값만 사용한다.

테이블 내에서 column 은 자주 중복 값을 포함한다. 때로는 서루 다른 (뚜렷한) 값만 나열할 때 사용한다.

> SELECT DISTINCT Syntax

```python
SELECT DISTINCT column1, column2, ...
FROM table_name
```

##### EXAMPLE

```python
SELECT Country FROM Customers;
Country
Germeny
Mexico
Mexico
UK
Sweden
Germany
...TOTAL 91 RECORDS
```
Customers 테이블의 country 필드를 출력하면 총 91개의 레코드를 확인할 수 있다.

그러나 SELECT DISTINCT 구문을 적용해 country 필드를 출력하면 21개의 레코드를 얻을 수 있다.

```python
SELECT DISTINCT Country FROM Customers;
Country
Germeny
Mexico
UK
Sweden
France
...TOTAL 21 RECORDS
SELECT COUNT(DISTINCT Country FROM Customers;
COUNT(DISTINCT Country)
21
```

COUNT() 함수를 이용하면 총 레코드의 수를 나타낼 수 있다.

### SQL WHERE 절
- WHERE 절은 레코드를 필터링 할 때 사용한다.
- WHERE 절은 지정된 조건을 충족하는 레코드만 추출할 때 사용한다.

> WHERE Syntax

```python
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```


##### EXAMPLE
```
SELECT *FROM Customers
WHERE Country='Mexicno';

CustomerID    CustomerName            ContactName    Address            City           PostalCode    Country
2             Ana Trujillo Empa..     Ana Trujillo   Avda. de la..      Mexico D.F.    05021         Mexico
3             Antonio Moreno Ta..     Antonio Mo..   Mataderos 2..      Mexico D.F.    05023         Mexico
...more

SELECT * FROM Customers
WHERE CustomerID=1;

CustomerID    CustomerName            ContactName    Address            City           PostalCode    Country
1             Alfreds Futterkiste     Maria Anders   Obere Str. 57      Berlin         12209         Germany
```
SQL은 텍스트 값에 대해 작은 따옴표를 사용해야 한다 (대부분의 데이터 베이스 시스템은 큰 따옴표도 허용한다).

** 그러나 숫자 값은 따옴표로 묶지 않아야한다.**

##### WHERE 절에서 쓰이는 연산자
Operator | Description
-------- | -----------
=        |  	Equal
<>       | Not Equal. Note: In some version of SQL this operator may be wrriten as !=
>        | Greater than
<        | Less than
>=       | Greater than or equal
<=       | Less than or equal
BETWEEN  | between inclusive range
LIKE     | Search for a pattern
IN       | To specifiy multiple possible values for a column

### SQL AND, OR, NOT 연산자
- WHERE 절은 AND, OR, NOT 연산자를 조합해서 사용할 수 있다.
- AND, OR 연산자는 둘 이상의 조건에 따라 레코드를 필터링 할 때 사용한다.
- AND로 구분된 모든 조건이 TRUE 이면 AND 연산자는 레코드를 표시한다.
- OR로 구분된 조건이 TRUE 인 경우 OR 연산자는 레코드를 표시한다.
- 조건이 참이 아닌 경우(거짓) 레코드를 표시한다.

> AND Syntax

```
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```

> OR Syntax

```
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```

> NOT Syntax

```
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition
```

##### EXAMPLE
```
SELECT * FROM Customers
WHERE Country='Germany' AND City='Berlin';

CustomerID    CustomerName            ContactName    Address            City           PostalCode    Country
1             Alfreds Futterkiste     Maria Anders   Obere Str. 57      Berlin         12209         Germany

SELECT * FROM Customers
WHERE City='Berlin' OR City='München';

CustomerID    CustomerName            ContactName          Address                City           PostalCode    Country
1             Alfreds Futterkiste     Maria Anders         Obere Str. 57          Berlin         12209         Germany
25            Frankenversand          Peter Franken        Berliner Platz 43      München        80805         Germany

SELECT * FROM Customers
WHERE NOT Country='Germany';

CustomerID    CustomerName            ContactName    Address            City           PostalCode    Country
2             Ana Trujillo Empa..     Ana Trujillo   Avda. de la..      Mexico D.F.    05021         Mexico
3             Antonio Moreno Ta..     Antonio Mo..   Mataderos 2..      Mexico D.F.    05023         Mexico
...TOTAL 80 RECORDS
```

### SQL ORDER BY Keyword
- ORDER BY 키워드는 RESULT-SET 을 오름차순 또는 내림차순으로 정렬할 때 사용한다.
- ORDER BY 키워드는 기본적으로 레코드를 오름차순으로 정렬한다.
- 내림차순으로 정렬하고 싶은 경우, DESC 키워드를 사용한다.

> ORDER BY Syntax

```
SELECT colunm1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```

##### EXAMPLE
```
SELECT * FROM Customers
ORDER BY Country

CustomerID    CustomerName          ContactName          Address          City             PostalCode       Country
12            Cactus Comidas...     Patricio Simpson     Cerrito 333      Buenos Aires     1010             Argentina
54            Océano Atlánti...     Yvonne Moncada       Ing. Gusta..     Buenos Airesl    1010             Argentina
...TOTAL 91 RECORDS

SELECT * FROM Customers
ORDER BY Country DESC;

CustomerID    CustomerName              ContactName        Address        City             PostalCode       Country
33            GROSELLA-Restaurante      Manuel Pereira     5ª Ave.        Caracas          1081             Venezuela
35            HILARIÓN-Abastos          Carlos Hernández   Carrera 22     San Cristóbal    5022             Venezuela
...TOTAL 91 RECORDS
```

### SQL INSERT INTO 구문
INSERT INTO 구문은 테이블에 새로운 레코드를 삽입할 때 사용한다.

> INSERT INTO Syntax

INSERT INTO 구문을 사용하는 방법은 2가지가 있다.

첫 번째 방법은 삽입할 column 이름과 값을 모두 지정하는 법이다.

테이블의 모든 column 에 값을 추가하는 경우, SQL 쿼리에서 column의 이름을 지정할 필요가 없다.

그러나 값의 순서가 테이블 안 colum 과 동일한지 확인해야 한다.

```
INSERT INTO table_name(column1, column2, column3, ...)
VALUES(value1, value2, value3, ...);
INSERT INTO table_name
VALUES(value1, value2, value3, ...);
```

### SQL NULL Value
> NULL 값은 무엇인가 ?

NULL 값이 있는 필드는 값어 없는 필드이다.

테이블 안 필드가 선택적이면, 필드에 값을 추가하지 않고 새로운 레코드를 삽입하거나 레코드를 업데이트 할 수 있다.

그 다음, 필드는 NULL 값으로 저장된다.

```
Note: NULL 값이  0 또는 공백이 있는 필드와 다른 것을 이해하는 것은 매우 중요하다.
NULL 값이 있는 필드는 레코드를 생성하는 동안 비어있는 필드이다.```

> NULL 값으 테스트하는 방법

=, <, <> 와 같은 비교 연산자로 NULL 값을 테스트 할 수 없다.

대신에 IS NULL 연산자와 IS NOT NULL 연산자를 사용해 테스트한다.

> IS NULL Syntax & IS NOT NULL

```
SELECT column_names
FROM table_name
WHERE column_name IS NULL;

SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```

### SQL UPDATE 구문

UPDATE 구문은 테이블 안 기존 레코드를 수정할 때 사용한다.

> UPDATE Syntax

```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

```
Note: 테이블에서 레코드를 UPDATE 할 때 주의하자!
UPDATE 문에서 WHERE 절을 확인한다. WHERE 절은 UPDATE 할 레코드를 지정한다.
만약 WHERE 절을 생략하면, 테이블 안 모든 레코드가 UPDATE 된다.
```

### SQL DELETE 구문

DELETE 구문은 테이블 안 레코드를 삭제할 때 사용한다.

> DELETE Syntax

```
DELETE FROM table_name
WHERE condition;
```

```
Note: 테이블 안 레코드를 삭제할 때 주의하자! DELETE 문에서 WHERE 절을 확인한다.
WHERE 절은 DELETE 할 레코드를 지정한다.
만약 WHERE 절을 생략하면, 테이블 안 모든 레코드가 DELETE된다.
```

##### 모든 레코드 삭제하기

테이블을 삭제하지 않고 테이블 안 모든 row를 삭제할 수 있다.

이것은 테이블의 구조, 속성, 인덱스가 손상되지 않는 것을 의미한다.

```
DELETE FROM table_name;
or
DELETE * FROM table_name;
```


### SQL SELECT TOP 절

SELECT TOP 절은 리턴할 레코드 수를 지정하는데 사용한다.

SELECT TOP 절은 수 천개의 레코드가 있는 큰 테이블에서 유용하다.

많은 수의 레코드를 리턴하면 성능에 영향을 줄 수 있기 때문이다.

```
Note: 모든 데이터 베이스 시스템이 SELECT TOP 절을 지원하지 않는다.
MySQL은 제한된 수의 레코드를 지원하기 위해 LIMIT 절을 지원하고, Oracle 은 ROWNUM 을 사용한다.
```

> SQL Server / MS Access Syntax

```
SELECT TOP number| PERCENT column_name(s)
FROM table_name
WHERE condition;
```
> MySQL Syntax

```
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
```

> Oracle Syntax

```
SELECT column_name(s)
FROM table_name
WHERE ROWNUM <= number;
```

##### EXAMPLE

```
일반적인 SELECT TOP
SELECT TOP 3 * FROM Customers;

MySQL SELECT TOP
SELECT * FROM Customers
LIMIT 3;

Oracle SELECT TOP
SELECT * FROM Customers
WHERE ROWNUM <= 3;
```

** 위의 SQL 명령문은 모두 같은 값을 리턴한다. **

### SQL MIN(), MAX() 기능

MIN() 기능은 선택된 column의 가장 작은 값을 리턴한다.

MAX() 기능은 선택된 column의 가장 큰 값을 리턴한다.

> MIN() Syntax

```
SELECT MIN(column_name)
FROM table_name
WHERE condition;
```

> MAX() Syntax

```
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```

##### EXAMPLE

```
SELECT MIN(Price) AS SmallestPrice
FROM Products;

SmallestPrice
2.5

SELECT MAN(Price) AS LargestPrice
FROM Products;

LargestPrice
263.5
```

### SQL COUNT(), AVG(), SUM() 기능

- COUNT() 기능은 지정된 기준과 일치하는 row 수를 리턴한다.

- AVG() 기능은 숫자 column의 평균 값을 리턴한다.

- SUM() 기능은 숫자 column의 총 합을 리턴한다.

> COUNT() Syntax

```
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```

> AVG() Syntax

```
SELECT AVG(column_name)
FROM table_name
WHERE condition;
```

> SUM() Syntax

```
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```

##### EXAMPLE
```
SELECT COUNT(ProductID)
FROM Products;

COUNT(ProductID)
77

SELECT AVG(Price)
FROM Products;

AVG(Price)
28.866363636363637


SELECT SUM(Quantity)
FROM OrderDetails;

SUM(Quantity)
12743
```

### SQL LIKE 연산자

LIKE 연산자는 WHERE 절에서 column의 지정된 패턴을 검색할 때 사용한다.

LIKE 연산자와 함께 사용하는 두 개의 와일드 카드가 있다.

> % : 백분율 기호는 0, 1 또는 복수 문자를 나타낸다.

>_ : 언더 스코어는 단일문자를 나타낸다.

```
Note: MS Access 는 `_` 대신 `?`를 사용한다.
```

백분율 기호와 언더 스코어를 조합하여 사용할 수 있다.

> LIKE Syntax

```
SELECT column1, column2, ...
FROM table_name
WHERE column LIKE pattern;

SELECT column1, column2, ...
FROM table_name
WHERE column NOT LIKE pattern;
```

** TIP : AND, OR 연산자를 사용하여 여러 조건을 조합할 수 있다. **

다음은 %와 _ 와일드 카드가 있는 다른 LIKE 여산자를 보여주는 예이다.

LIKE Operation                         | Description
--------------                         | ---------------
WHERE CustomerName LIKE ‘a%’ | a로 시작하는 값을 찾는다.
WHERE CustomerName LIKE ‘%a’ | 	a로 끝나는 값을 찾는다.
WHERE CustomerName LIKE ‘%or%’ | 임의의 위치에 있는 or 값을 찾는다.
WHERE CustomerName LIKE ‘_r%’ | 	두 번째 위치에 r이 있는 값을 찾는다.
WHERE CustomerName LIKE ‘a_%_%’ | a로 시작하고 최소 길이가 3글자 이상인 값을 찾는다.
WHERE CustomerName LIKE ‘a%o’  | a로 시작하고 o로 끝나는 값을 찾는다.

##### EXAMPLE
```
SELECT * FROM Customers
WHERE CustomerName LIKE 'a%';

CustomerID    CustomerName            ContactName    Address            City           PostalCode    Country
1             Alfreds Futterkiste     Maria Anders   Obere Str. 57      Berlin         12209         Germany
2             Ana Trujillo Empa..     Ana Trujillo   Avda. de la..      Mexico D.F.    05021         Mexico
...TOTAL 4 RECORDS
```

### SQL 와일드 카드 문자
와일드 카드 문자는 문자열의 다른 문자를 대체할 때 사용한다.

와일드 카드 문자는 SQL LIKE 연산자와 같이 사용한다.

LIKE 연산자는 WHERE 절에서 column 에 지정된 패턴을 검색하는데 사용한다.

LIKE 연산자와 함께 사용하는 두 개의 와일드 카드가 있다.

> % : 백분율 기호는 0, 1 또는 복수 문자를 나타낸다.

>_ : 언더 스코어는 단일문자를 나타낸다.

```
Note: MS Access는 언더스코어[_] 대신에 물음표[?]를 사용한다.
```

MS Access, SQL Server 에서 다음과 같이 사용한다.

> [charlist] : 일치 시킬 문자와 세트의 범위를 지정한다.

> [^charlist] or [!charlist] : 일치하지 않는 문자의 집합과 범위를 지정한다.

LIKE Operation      | Description
-------------------|-------------------
WHERE CustomerName LIKE ‘a%’ | a로 시작하는 값을 찾는다.
WHERE CustomerName LIKE ‘%a’ | 	a로 끝나는 값을 찾는다.
WHERE CustomerName LIKE ‘%or%’ | 임의의 위치에 있는 or 값을 찾는다.
WHERE CustomerName LIKE ‘_r%’ | 두 번째 위치에 r이 있는 값을 찾는다.
WHERE CustomerName LIKE ‘a_%_%’ | a로 시작하고 최소 길이가 3글자 이상인 값을 찾는다.
WHERE CustomerName LIKE ‘a%o’ | a로 시작하고 o로 끝나는 값을 찾는다.

### SQL IN 연산자
IN 연산자를 사용해 WHERE 절에 여러 가지 값을 지정할 수 있다.

IN 연산자는 OR를 한 번 이상 사용한 조건의 줄임말이다.

> IN Syntax

```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);

SELECT column_name(s)
FROM table_name
WHERE column_name NOT IN (value1, value2, ...);

or

SELECT column_name(s)
FROM table_name
WHERE column_name IN (SELECT STATEMENT);
```
##### EXAMPLE

```
SELECT * FROM Customers
WHERE Country IN ('Germany', 'France', 'UK');

CustomerID    CustomerName            ContactName     Address               City           PostalCode    Country
1             Alfreds Futterkiste     Maria Anders    Obere Str. 57         Berlin         12209         Germany
4             Around the Horn         Thomas  Hardy   120  Hanover Sq.      London         WA1 1DP       UK
...TOTAL 29 RECORDS

```

### SQL BETWEEN 연산자
BETWEEN 연산자는 주어진 범위 내의 값을 선택한다.

값은 숫자, 텍스트, 날짜 일 수 있다.

BETWEEN 연산자는 시작과 끝 값이 포함된다.

> BETWEEN Syntax

```
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;

SELECT column_name(s)
FROM table_name
WHERE column_name NOT BETWEEN value1 AND value2;
```
##### EXAMPLE
```
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20;

ProductID     ProductName    SupplierID     CategoryID     Unit                    Price
1             Chais          1              1              10 boxes x 20 bags      18
2             Chang          1              1              24 - 12 oz bottles      19
...TOTAL 29 RECORDS
```
### SQL Aliases

SQL Aliases 는 테이블 또는 `column` 에 임시적인 이름을 지정하는데 사용한다.

Alias 는 `column` 의 이름을 쉽게 보이기 위해 자주 사용한다.

Alias 는 쿼리가 조회되는 동안 존재한다.

> Alias Column Syntax

```
SELECT column_name AS alias_name
FROM talbe_name
```

> Alias Table Syntax

```
SELECT column_name(s)
FROM table_name AS alias_name
```

##### EXAMPLE

```
SELECT CustomerID AS ID, CustomerName AS Customer
FROM Customers;

Note: alias 에 공백이 있을 경우 대괄호 혹은 큰 따옴표가 필요하다.
SELECT CustomerName AS Customer, ContactName AS [Contace Person]
FROM Customers;
```

### SQL JOIN

JOIN 절은 2개 이상의 테이블(서로 관련된 column이 있었을 때)에 있는 `row` 를 조합할 때 사용한다.

##### SQL JOIN 의 다양한 형태
- (INNER) JOIN : 두 테이블에서 값이 일치하는 레코드를 리턴한다.

- LEFT (OUTER) JOIN : 왼쪽 테이블에서 모든 레코드를 리턴하고 오른쪽 테이블에서 일치하는 레코드를 리턴한다.

- RIGHT (OUTER) JOIN : 오른쪽 테이블에서 모든 레코드를 리턴하고 왼쪽 테이블에서 일치하는 레코드를 리턴한다.
- FULL (OUTER) JOIN : 왼쪽 또는 오른쪽 테이블이 일치하는 항목이 있으면 모든 레코드를 리턴한다.

### SQL INNER JOIN 키워드
INNER JOIN 키워드는 두 테이블에서 일치하는 값을 가진 레코드를 리턴한다.

> INNER JOIN Syntax

```
SELECT column_name(s)
FROM table1
INNER JOIN table2 ON table1.column_name = table2.column_name;
```
### SQL LEFT JOIN 키워드

LEFT JOIN 키워드는 왼쪽 테이블(table1)의 모든 레코드와 오른쪽 테이블(table2)의 일치하는 레코드를 리턴한다.

일치하는 값이 없으면 오른쪽 결과에서 NULL 이 출력된다.

> LEFT JOIN Syntax

```
SELECT column_name(s)
FROM table1
LEFT JOIN table2 ON table1.column_name = table2.column_name;
```
** Note: 다른 데이터 베이스에서는 LEFT JOIN을 LEFT OUTER JOIN으로 부른다. **

### SQL RIGHT JOIN 키워드
RIGHT JOIN 키워드는 오른쪽 테이블(table2)의 모든 레코드와 왼쪽 테이블(table1)의 일치하는 레코드를 리턴한다.

일치하는 값이 없는 경우 왼쪽에서 NULL이 출력된다.

> RIGHT JOIN Syntax

```
SELECT column_name(s)
FROM table1
RIGHT JOIN table2 ON table1.column_name = table2.column_name;
```

** Note: 다른 데이터 베이스에서는 RIGHT JOIN을 RIGHT OUTER JOIN으로 부른다. **

### FULL OUTER JOIN 키워드

FULL OUTER JOIN 키워드는 왼쪽(table1) 또는 오른쪽(table2) 테이블에 레코드가 일치하는 경우

모든 레코드를 리턴한다

`Note: FULL OUTER JOIN 은 잠재적으로 매우 큰 RESULT-SET 을 리턴할 수 있다.`

> FULL OUTER JOIN Syntax

```
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2 ON table1.column_name = table2.column_name;
```

### SQL Self JOIN
Self JOIN은 정규 JOIN이다.

> Self JOIN Syntax

```
SELECT column_name(s)
FROM table1 T1, table2 T2
WHERE condition;
```

### SQL UNION 연산자
UNION 연산자는 두 개 이상의 SELECT 구문 RESULT-SET을 결합할 때 사용한다.

UNION 내 각 SELECT 구문은 같은 수의 column을 가져야 한다.

column 은 유사한 데이터 타입이어야 한다.

각 SELECT 구문의 column은 같은 순서로 있어야 한다.

> UNION Syntax

```
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM talbe2;
```
UNION 연산자는 기본적으로 고유한 값만 선택한다. 중복된 값을 허용하려면, UNION ALL 을 사용해야 한다.

> UNION ALL Syntax

```
SELECT column_name(s) FROM table1
UNION ALL
SELECT column_name(s) FROM table2;
```

** Note: RESULT-SET 안 column 은 일반적으로 UNION 의 첫 번째 SELECT 구문의 column 의 이름과 같다. **

### SQL GROUP BY 구문
GROUP BY 구문은 집계 함수(COUNT, MAX, MIN, SUM, AVG) 와 함께 사용되어

RESULT-SET 을 하나 이상의 column 으로 그룹화 한다.

> GROUP BY Syntax

```
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);
```

### SQL HAVING 절

WHERE키워드는 집계 함수와 사용할 수 없기 때문에, HAVING 절이 SQL에 추가됐다.

> HAVING Syntax

```
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s);
```

### SQL EXISTS 연산자

EXISTS 연산자는 서브 쿼리 안 레코드가 존재하는지 테스트하는데 사용한다.

EXISTS 연산자는 서브 쿼리가 하나 이상의 레코드가 존재하면 TRUE 값을 리턴한다.

> EXISTS Syntax

```
SELECT column_name(s)
FROM table_name
WHERE EXISTS
(SELECT column_name FROM table_name WHERE condition);
```


  CustomerID    CustomerName            ContactName    Address            City           PostalCode    Country
  1             Alfreds Futterkiste     Maria Anders   Obere Str. 57      Berlin         12209         Germany
  2             Ana Trujillo Empa..     Ana Trujillo   Avda. de la..      Mexico D.F.    05021         Mexico
  ...more
  ```
- 모든 테이블 은 `필드` 라는 더 작은 엔티티로 나뉜다. **Customers** 테이블의 `필드`는 **CustomerID, CustomerName, ContactName, Address, City, PostalCode, Country** 구성되어 있다. `필드`는 테이블의 모든 레코드에 대한 특정 정보를 유지하고 관리하도록 설계된 `테이블의 열`이다. 열(이 또한 레코드)은 테이블 안에서 `개별적인 항목으로 존재`한다. 위 91개의 레코드를 가진 **Customers** 테이블을 예를 들어보자. `테이블의 수평(가로)` 엔티티는 `레코드`다. `테이블의 수직(세로)` 엔티티인 column열은 테이블의 `특정 필드와 연관된 정보`를 갖고 있다.
---

### SQL Syntax
- `데이터 베이스`는 하나 이상의 `테이블`을 포함한다. 각 테이블은 이름(예: ‘Customers’ or ‘Orders’)으로 확인한다. 그리고 `테이블`은 데이터가 있는 `레코드(row)를 포함`한다.

- 튜토리얼에서는 잘 알려진 Northwind 샘플 데이터베이스를 사용한다.

### 잊지말기!
- `SQL 키워드`는 `대소문자`를 `구분하지 않는다`.
- `select` 와 `SELECT` 는 `같은 것을 의미`한다.
- **W3School 튜토리얼`에서는 모든 SQL 키워드를 대문자로 작성**한다.

### SQL구문 뒤에 오는 세미콜론 (;)
- 몇몇 데이터 베이스 시스템은 SQL `구문이 끝난 후` **세미콜론**을 적어야한다.
- `세미콜론`은 데이터 베이스 시스템에서 **둘 이상의 각각의 SQL 구문을 분리하는 표준방법**이다.
- **w3School 튜토리얼에서는 각 SQL 구문마다 세미콜론을 사용**한다.

### 가장 중요한 SQL 명령 중 일부
- SELECT : 데이터 베이스에서 데이터를 추출한다.
- UPDATE : 데이터 베이스의 데이터를 변경(업데이트)한다.
- DELETE : 데이터 베이스의 데이터를 삭제한다.
- INSERT INTO : 데이터 베이스에 새로운 데이터를 저장(삽입)한다.
- CREATE DATABASE : 새로운 데이터 베이스를 생성한다.
- ALTER DATABASE : 데이터 베이스를 수정한다.
- CREATE TABLE : 새로운 테이블 생성한다.
- ALTER TABLE : 테이블을 수정한다.
- DELETE TABLE : 테이블을 삭제한다.
- CREATE INDEX : 색인(검색 키)를 생성한다.
- DROP INDEX : 색인을 삭제한다.


### SQL SELECT 구문
- SELECT 구문은 데이터 베이스에서 데이터를 선택하는데 사용한다.
- 리턴된 데이터는 RESULT-SET 이라고 하는 결과 테이블에 저장된다.
> SELECT Syntax

  ```python
  SELECT column1, column2, ...
  FROM table_name
  ```
 - 여기에서 column1, column2, …는 데이터를 선택할 테이블의 필드 이름이다.
 - 표에서 사용 가능한 모든 필드를 선택하려면 다음 구문을 사용한다.
 ```python
 SELECT * FROM table_name;
 ```

### SQL SELECT DISTINCT 구문
SELECT DISTINCT 은 고유한 (다른) 값만 사용한다.

테이블 내에서 column 은 자주 중복 값을 포함한다. 때로는 서루 다른 (뚜렷한) 값만 나열할 때 사용한다.

> SELECT DISTINCT Syntax

```python
SELECT DISTINCT column1, column2, ...
FROM table_name
```

##### EXAMPLE

```python
SELECT Country FROM Customers;
Country
Germeny
Mexico
Mexico
UK
Sweden
Germany
...TOTAL 91 RECORDS
```
Customers 테이블의 country 필드를 출력하면 총 91개의 레코드를 확인할 수 있다.

그러나 SELECT DISTINCT 구문을 적용해 country 필드를 출력하면 21개의 레코드를 얻을 수 있다.

```python
SELECT DISTINCT Country FROM Customers;
Country
Germeny
Mexico
UK
Sweden
France
...TOTAL 21 RECORDS
SELECT COUNT(DISTINCT Country FROM Customers;
COUNT(DISTINCT Country)
21
```

COUNT() 함수를 이용하면 총 레코드의 수를 나타낼 수 있다.

### SQL WHERE 절
- WHERE 절은 레코드를 필터링 할 때 사용한다.
- WHERE 절은 지정된 조건을 충족하는 레코드만 추출할 때 사용한다.

> WHERE Syntax

```python
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```


##### EXAMPLE
```
SELECT *FROM Customers
WHERE Country='Mexicno';

CustomerID    CustomerName            ContactName    Address            City           PostalCode    Country
2             Ana Trujillo Empa..     Ana Trujillo   Avda. de la..      Mexico D.F.    05021         Mexico
3             Antonio Moreno Ta..     Antonio Mo..   Mataderos 2..      Mexico D.F.    05023         Mexico
...more

SELECT * FROM Customers
WHERE CustomerID=1;

CustomerID    CustomerName            ContactName    Address            City           PostalCode    Country
1             Alfreds Futterkiste     Maria Anders   Obere Str. 57      Berlin         12209         Germany
```
SQL은 텍스트 값에 대해 작은 따옴표를 사용해야 한다 (대부분의 데이터 베이스 시스템은 큰 따옴표도 허용한다).

** 그러나 숫자 값은 따옴표로 묶지 않아야한다.**

##### WHERE 절에서 쓰이는 연산자
Operator | Description
-------- | -----------
=        |  	Equal
<>       | Not Equal. Note: In some version of SQL this operator may be wrriten as !=
>        | Greater than
<        | Less than
>=       | Greater than or equal
<=       | Less than or equal
BETWEEN  | between inclusive range
LIKE     | Search for a pattern
IN       | To specifiy multiple possible values for a column

### SQL AND, OR, NOT 연산자
- WHERE 절은 AND, OR, NOT 연산자를 조합해서 사용할 수 있다.
- AND, OR 연산자는 둘 이상의 조건에 따라 레코드를 필터링 할 때 사용한다.
- AND로 구분된 모든 조건이 TRUE 이면 AND 연산자는 레코드를 표시한다.
- OR로 구분된 조건이 TRUE 인 경우 OR 연산자는 레코드를 표시한다.
- 조건이 참이 아닌 경우(거짓) 레코드를 표시한다.

> AND Syntax

```
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```

> OR Syntax

```
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```

> NOT Syntax

```
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition
```

##### EXAMPLE
```
SELECT * FROM Customers
WHERE Country='Germany' AND City='Berlin';

CustomerID    CustomerName            ContactName    Address            City           PostalCode    Country
1             Alfreds Futterkiste     Maria Anders   Obere Str. 57      Berlin         12209         Germany

SELECT * FROM Customers
WHERE City='Berlin' OR City='München';

CustomerID    CustomerName            ContactName          Address                City           PostalCode    Country
1             Alfreds Futterkiste     Maria Anders         Obere Str. 57          Berlin         12209         Germany
25            Frankenversand          Peter Franken        Berliner Platz 43      München        80805         Germany

SELECT * FROM Customers
WHERE NOT Country='Germany';

CustomerID    CustomerName            ContactName    Address            City           PostalCode    Country
2             Ana Trujillo Empa..     Ana Trujillo   Avda. de la..      Mexico D.F.    05021         Mexico
3             Antonio Moreno Ta..     Antonio Mo..   Mataderos 2..      Mexico D.F.    05023         Mexico
...TOTAL 80 RECORDS
```

### SQL ORDER BY Keyword
- ORDER BY 키워드는 RESULT-SET 을 오름차순 또는 내림차순으로 정렬할 때 사용한다.
- ORDER BY 키워드는 기본적으로 레코드를 오름차순으로 정렬한다.
- 내림차순으로 정렬하고 싶은 경우, DESC 키워드를 사용한다.

> ORDER BY Syntax

```
SELECT colunm1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```

##### EXAMPLE
```
SELECT * FROM Customers
ORDER BY Country

CustomerID    CustomerName          ContactName          Address          City             PostalCode       Country
12            Cactus Comidas...     Patricio Simpson     Cerrito 333      Buenos Aires     1010             Argentina
54            Océano Atlánti...     Yvonne Moncada       Ing. Gusta..     Buenos Airesl    1010             Argentina
...TOTAL 91 RECORDS

SELECT * FROM Customers
ORDER BY Country DESC;

CustomerID    CustomerName              ContactName        Address        City             PostalCode       Country
33            GROSELLA-Restaurante      Manuel Pereira     5ª Ave.        Caracas          1081             Venezuela
35            HILARIÓN-Abastos          Carlos Hernández   Carrera 22     San Cristóbal    5022             Venezuela
...TOTAL 91 RECORDS
```

### SQL INSERT INTO 구문
INSERT INTO 구문은 테이블에 새로운 레코드를 삽입할 때 사용한다.

> INSERT INTO Syntax

INSERT INTO 구문을 사용하는 방법은 2가지가 있다.

첫 번째 방법은 삽입할 column 이름과 값을 모두 지정하는 법이다.

테이블의 모든 column 에 값을 추가하는 경우, SQL 쿼리에서 column의 이름을 지정할 필요가 없다.

그러나 값의 순서가 테이블 안 colum 과 동일한지 확인해야 한다.

```
INSERT INTO table_name(column1, column2, column3, ...)
VALUES(value1, value2, value3, ...);
INSERT INTO table_name
VALUES(value1, value2, value3, ...);
```

### SQL NULL Value
> NULL 값은 무엇인가 ?

NULL 값이 있는 필드는 값어 없는 필드이다.

테이블 안 필드가 선택적이면, 필드에 값을 추가하지 않고 새로운 레코드를 삽입하거나 레코드를 업데이트 할 수 있다.

그 다음, 필드는 NULL 값으로 저장된다.

```
Note: NULL 값이  0 또는 공백이 있는 필드와 다른 것을 이해하는 것은 매우 중요하다.
NULL 값이 있는 필드는 레코드를 생성하는 동안 비어있는 필드이다.```

> NULL 값으 테스트하는 방법

=, <, <> 와 같은 비교 연산자로 NULL 값을 테스트 할 수 없다.

대신에 IS NULL 연산자와 IS NOT NULL 연산자를 사용해 테스트한다.

> IS NULL Syntax & IS NOT NULL

```
SELECT column_names
FROM table_name
WHERE column_name IS NULL;

SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```

### SQL UPDATE 구문

UPDATE 구문은 테이블 안 기존 레코드를 수정할 때 사용한다.

> UPDATE Syntax

```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

```
Note: 테이블에서 레코드를 UPDATE 할 때 주의하자!
UPDATE 문에서 WHERE 절을 확인한다. WHERE 절은 UPDATE 할 레코드를 지정한다.
만약 WHERE 절을 생략하면, 테이블 안 모든 레코드가 UPDATE 된다.
```

### SQL DELETE 구문

DELETE 구문은 테이블 안 레코드를 삭제할 때 사용한다.

> DELETE Syntax

```
DELETE FROM table_name
WHERE condition;
```

```
Note: 테이블 안 레코드를 삭제할 때 주의하자! DELETE 문에서 WHERE 절을 확인한다.
WHERE 절은 DELETE 할 레코드를 지정한다.
만약 WHERE 절을 생략하면, 테이블 안 모든 레코드가 DELETE된다.
```

##### 모든 레코드 삭제하기

테이블을 삭제하지 않고 테이블 안 모든 row를 삭제할 수 있다.

이것은 테이블의 구조, 속성, 인덱스가 손상되지 않는 것을 의미한다.

```
DELETE FROM table_name;
or
DELETE * FROM table_name;
```


### SQL SELECT TOP 절

SELECT TOP 절은 리턴할 레코드 수를 지정하는데 사용한다.

SELECT TOP 절은 수 천개의 레코드가 있는 큰 테이블에서 유용하다.

많은 수의 레코드를 리턴하면 성능에 영향을 줄 수 있기 때문이다.

```
Note: 모든 데이터 베이스 시스템이 SELECT TOP 절을 지원하지 않는다.
MySQL은 제한된 수의 레코드를 지원하기 위해 LIMIT 절을 지원하고, Oracle 은 ROWNUM 을 사용한다.
```

> SQL Server / MS Access Syntax

```
SELECT TOP number| PERCENT column_name(s)
FROM table_name
WHERE condition;
```
> MySQL Syntax

```
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
```

> Oracle Syntax

```
SELECT column_name(s)
FROM table_name
WHERE ROWNUM <= number;
```

##### EXAMPLE

```
일반적인 SELECT TOP
SELECT TOP 3 * FROM Customers;

MySQL SELECT TOP
SELECT * FROM Customers
LIMIT 3;

Oracle SELECT TOP
SELECT * FROM Customers
WHERE ROWNUM <= 3;
```

** 위의 SQL 명령문은 모두 같은 값을 리턴한다. **

### SQL MIN(), MAX() 기능

MIN() 기능은 선택된 column의 가장 작은 값을 리턴한다.

MAX() 기능은 선택된 column의 가장 큰 값을 리턴한다.

> MIN() Syntax

```
SELECT MIN(column_name)
FROM table_name
WHERE condition;
```

> MAX() Syntax

```
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```

##### EXAMPLE

```
SELECT MIN(Price) AS SmallestPrice
FROM Products;

SmallestPrice
2.5

SELECT MAN(Price) AS LargestPrice
FROM Products;

LargestPrice
263.5
```

### SQL COUNT(), AVG(), SUM() 기능

- COUNT() 기능은 지정된 기준과 일치하는 row 수를 리턴한다.

- AVG() 기능은 숫자 column의 평균 값을 리턴한다.

- SUM() 기능은 숫자 column의 총 합을 리턴한다.

> COUNT() Syntax

```
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```

> AVG() Syntax

```
SELECT AVG(column_name)
FROM table_name
WHERE condition;
```

> SUM() Syntax

```
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```

##### EXAMPLE
```
SELECT COUNT(ProductID)
FROM Products;

COUNT(ProductID)
77

SELECT AVG(Price)
FROM Products;

AVG(Price)
28.866363636363637


SELECT SUM(Quantity)
FROM OrderDetails;

SUM(Quantity)
12743
```

### SQL LIKE 연산자

LIKE 연산자는 WHERE 절에서 column의 지정된 패턴을 검색할 때 사용한다.

LIKE 연산자와 함께 사용하는 두 개의 와일드 카드가 있다.

> % : 백분율 기호는 0, 1 또는 복수 문자를 나타낸다.

>_ : 언더 스코어는 단일문자를 나타낸다.

```
Note: MS Access 는 `_` 대신 `?`를 사용한다.
```

백분율 기호와 언더 스코어를 조합하여 사용할 수 있다.

> LIKE Syntax

```
SELECT column1, column2, ...
FROM table_name
WHERE column LIKE pattern;

SELECT column1, column2, ...
FROM table_name
WHERE column NOT LIKE pattern;
```

** TIP : AND, OR 연산자를 사용하여 여러 조건을 조합할 수 있다. **

다음은 %와 _ 와일드 카드가 있는 다른 LIKE 여산자를 보여주는 예이다.

LIKE Operation                         | Description
--------------                         | ---------------
WHERE CustomerName LIKE ‘a%’ | a로 시작하는 값을 찾는다.
WHERE CustomerName LIKE ‘%a’ | 	a로 끝나는 값을 찾는다.
WHERE CustomerName LIKE ‘%or%’ | 임의의 위치에 있는 or 값을 찾는다.
WHERE CustomerName LIKE ‘_r%’ | 	두 번째 위치에 r이 있는 값을 찾는다.
WHERE CustomerName LIKE ‘a_%_%’ | a로 시작하고 최소 길이가 3글자 이상인 값을 찾는다.
WHERE CustomerName LIKE ‘a%o’  | a로 시작하고 o로 끝나는 값을 찾는다.

##### EXAMPLE
```
SELECT * FROM Customers
WHERE CustomerName LIKE 'a%';

CustomerID    CustomerName            ContactName    Address            City           PostalCode    Country
1             Alfreds Futterkiste     Maria Anders   Obere Str. 57      Berlin         12209         Germany
2             Ana Trujillo Empa..     Ana Trujillo   Avda. de la..      Mexico D.F.    05021         Mexico
...TOTAL 4 RECORDS
```

### SQL 와일드 카드 문자
와일드 카드 문자는 문자열의 다른 문자를 대체할 때 사용한다.

와일드 카드 문자는 SQL LIKE 연산자와 같이 사용한다.

LIKE 연산자는 WHERE 절에서 column 에 지정된 패턴을 검색하는데 사용한다.

LIKE 연산자와 함께 사용하는 두 개의 와일드 카드가 있다.

> % : 백분율 기호는 0, 1 또는 복수 문자를 나타낸다.

>_ : 언더 스코어는 단일문자를 나타낸다.

```
Note: MS Access는 언더스코어[_] 대신에 물음표[?]를 사용한다.
```

MS Access, SQL Server 에서 다음과 같이 사용한다.

> [charlist] : 일치 시킬 문자와 세트의 범위를 지정한다.

> [^charlist] or [!charlist] : 일치하지 않는 문자의 집합과 범위를 지정한다.

LIKE Operation      | Description
-------------------|-------------------
WHERE CustomerName LIKE ‘a%’ | a로 시작하는 값을 찾는다.
WHERE CustomerName LIKE ‘%a’ | 	a로 끝나는 값을 찾는다.
WHERE CustomerName LIKE ‘%or%’ | 임의의 위치에 있는 or 값을 찾는다.
WHERE CustomerName LIKE ‘_r%’ | 두 번째 위치에 r이 있는 값을 찾는다.
WHERE CustomerName LIKE ‘a_%_%’ | a로 시작하고 최소 길이가 3글자 이상인 값을 찾는다.
WHERE CustomerName LIKE ‘a%o’ | a로 시작하고 o로 끝나는 값을 찾는다.

### SQL IN 연산자
IN 연산자를 사용해 WHERE 절에 여러 가지 값을 지정할 수 있다.

IN 연산자는 OR를 한 번 이상 사용한 조건의 줄임말이다.

> IN Syntax

```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);

SELECT column_name(s)
FROM table_name
WHERE column_name NOT IN (value1, value2, ...);

or

SELECT column_name(s)
FROM table_name
WHERE column_name IN (SELECT STATEMENT);
```
##### EXAMPLE

```
SELECT * FROM Customers
WHERE Country IN ('Germany', 'France', 'UK');

CustomerID    CustomerName            ContactName     Address               City           PostalCode    Country
1             Alfreds Futterkiste     Maria Anders    Obere Str. 57         Berlin         12209         Germany
4             Around the Horn         Thomas  Hardy   120  Hanover Sq.      London         WA1 1DP       UK
...TOTAL 29 RECORDS

```

### SQL BETWEEN 연산자
BETWEEN 연산자는 주어진 범위 내의 값을 선택한다.

값은 숫자, 텍스트, 날짜 일 수 있다.

BETWEEN 연산자는 시작과 끝 값이 포함된다.

> BETWEEN Syntax

```
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;

SELECT column_name(s)
FROM table_name
WHERE column_name NOT BETWEEN value1 AND value2;
```
##### EXAMPLE
```
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20;

ProductID     ProductName    SupplierID     CategoryID     Unit                    Price
1             Chais          1              1              10 boxes x 20 bags      18
2             Chang          1              1              24 - 12 oz bottles      19
...TOTAL 29 RECORDS
```
### SQL Aliases

SQL Aliases 는 테이블 또는 `column` 에 임시적인 이름을 지정하는데 사용한다.

Alias 는 `column` 의 이름을 쉽게 보이기 위해 자주 사용한다.

Alias 는 쿼리가 조회되는 동안 존재한다.

> Alias Column Syntax

```
SELECT column_name AS alias_name
FROM talbe_name
```

> Alias Table Syntax

```
SELECT column_name(s)
FROM table_name AS alias_name
```

##### EXAMPLE

```
SELECT CustomerID AS ID, CustomerName AS Customer
FROM Customers;

Note: alias 에 공백이 있을 경우 대괄호 혹은 큰 따옴표가 필요하다.
SELECT CustomerName AS Customer, ContactName AS [Contace Person]
FROM Customers;
```

### SQL JOIN

JOIN 절은 2개 이상의 테이블(서로 관련된 column이 있었을 때)에 있는 `row` 를 조합할 때 사용한다.

##### SQL JOIN 의 다양한 형태
- (INNER) JOIN : 두 테이블에서 값이 일치하는 레코드를 리턴한다.

- LEFT (OUTER) JOIN : 왼쪽 테이블에서 모든 레코드를 리턴하고 오른쪽 테이블에서 일치하는 레코드를 리턴한다.

- RIGHT (OUTER) JOIN : 오른쪽 테이블에서 모든 레코드를 리턴하고 왼쪽 테이블에서 일치하는 레코드를 리턴한다.
- FULL (OUTER) JOIN : 왼쪽 또는 오른쪽 테이블이 일치하는 항목이 있으면 모든 레코드를 리턴한다.

### SQL INNER JOIN 키워드
INNER JOIN 키워드는 두 테이블에서 일치하는 값을 가진 레코드를 리턴한다.

> INNER JOIN Syntax

```
SELECT column_name(s)
FROM table1
INNER JOIN table2 ON table1.column_name = table2.column_name;
```
### SQL LEFT JOIN 키워드

LEFT JOIN 키워드는 왼쪽 테이블(table1)의 모든 레코드와 오른쪽 테이블(table2)의 일치하는 레코드를 리턴한다.

일치하는 값이 없으면 오른쪽 결과에서 NULL 이 출력된다.

> LEFT JOIN Syntax

```
SELECT column_name(s)
FROM table1
LEFT JOIN table2 ON table1.column_name = table2.column_name;
```
** Note: 다른 데이터 베이스에서는 LEFT JOIN을 LEFT OUTER JOIN으로 부른다. **

### SQL RIGHT JOIN 키워드
RIGHT JOIN 키워드는 오른쪽 테이블(table2)의 모든 레코드와 왼쪽 테이블(table1)의 일치하는 레코드를 리턴한다.

일치하는 값이 없는 경우 왼쪽에서 NULL이 출력된다.

> RIGHT JOIN Syntax

```
SELECT column_name(s)
FROM table1
RIGHT JOIN table2 ON table1.column_name = table2.column_name;
```

** Note: 다른 데이터 베이스에서는 RIGHT JOIN을 RIGHT OUTER JOIN으로 부른다. **

### FULL OUTER JOIN 키워드

FULL OUTER JOIN 키워드는 왼쪽(table1) 또는 오른쪽(table2) 테이블에 레코드가 일치하는 경우

모든 레코드를 리턴한다

`Note: FULL OUTER JOIN 은 잠재적으로 매우 큰 RESULT-SET 을 리턴할 수 있다.`

> FULL OUTER JOIN Syntax

```
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2 ON table1.column_name = table2.column_name;
```

### SQL Self JOIN
Self JOIN은 정규 JOIN이다.

> Self JOIN Syntax

```
SELECT column_name(s)
FROM table1 T1, table2 T2
WHERE condition;
```

### SQL UNION 연산자
UNION 연산자는 두 개 이상의 SELECT 구문 RESULT-SET을 결합할 때 사용한다.

UNION 내 각 SELECT 구문은 같은 수의 column을 가져야 한다.

column 은 유사한 데이터 타입이어야 한다.

각 SELECT 구문의 column은 같은 순서로 있어야 한다.

> UNION Syntax

```
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM talbe2;
```
UNION 연산자는 기본적으로 고유한 값만 선택한다. 중복된 값을 허용하려면, UNION ALL 을 사용해야 한다.

> UNION ALL Syntax

```
SELECT column_name(s) FROM table1
UNION ALL
SELECT column_name(s) FROM table2;
```

** Note: RESULT-SET 안 column 은 일반적으로 UNION 의 첫 번째 SELECT 구문의 column 의 이름과 같다. **

### SQL GROUP BY 구문
GROUP BY 구문은 집계 함수(COUNT, MAX, MIN, SUM, AVG) 와 함께 사용되어

RESULT-SET 을 하나 이상의 column 으로 그룹화 한다.

> GROUP BY Syntax

```
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);
```

### SQL HAVING 절

WHERE키워드는 집계 함수와 사용할 수 없기 때문에, HAVING 절이 SQL에 추가됐다.

> HAVING Syntax

```
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s);
```

### SQL EXISTS 연산자

EXISTS 연산자는 서브 쿼리 안 레코드가 존재하는지 테스트하는데 사용한다.

EXISTS 연산자는 서브 쿼리가 하나 이상의 레코드가 존재하면 TRUE 값을 리턴한다.

> EXISTS Syntax

```
SELECT column_name(s)
FROM table_name
WHERE EXISTS
(SELECT column_name FROM table_name WHERE condition);
```
