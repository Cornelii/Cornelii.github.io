---
layout: post
title: "Oracle SQL"
author-id: "Cornelii. G. Son"
tags: [study, oracle, oracle sql]
updated: "2020-03-01"
comments: true
chapter: "1"
en_title: "Summary sql of oracledb"
hide_chapter: true
---

## SQL (Structured Query Language)
보통 RDBMS (Relational Database Management System)에서 데이터를 읽고, 쓰거나 Database의 구조를 
관리하는데 쓰는 문법/언어입니다. 표준화가 잘 되어 있기 때문에 DBMS에 따른 큰 차이는 없습니다.
<br/><br/>

<div id="main_list"></div>

## Database Objects
 - <a href="#table">Table</a>
 - <a href="#view">View</a>
 - <a href="#index">Index</a>
 - <a href="#synonym">Synonym</a>
 - <a href="#seq">Sequence</a>
 - <a href="#fcn">Function</a>
 - <a href="#proc">Procedure</a>
 - <a href="#package">Package</a>
<br/><br/>

<div id="table"></div>

#### - <a href="#main_list">Table</a>
Table은 데이터를 담고 있는 가장 기본적인 객체입니다. 행(row)과 열(column)의 2차원 형태로 구성되어 있고, 엑셀의 Sheet를 떠올리시면 됩니다.
<br/>

**TABLE의 기본적인 선언**

```sql
CREATE TABLE TEST_TABLE (
    COL1_NAME  COL1_DATATYPE,
    COL2_NAME  COL2_DATATYPE NULL,
    COL3_NAME  COL3_DATATYPE NOT NULL,
    COL4_NAME  COL4_DATATYPE DEFAULT DEFAULT_VALUE NOT NULL,
    ETC...
);
```
<br/>

##### i. Data Type for table column
- Data Type|Description|Remarks
 --|--|--
 CHAR|Fixed-Length String|
VARCHAR|Variable-Length String|
NCHAR|Fixed-Length String for Unicode|
NVARCHAR2|Variable-Length String for Unicode|
LONG|Variable-Length Large String| Maximum 2GB, Barely Used
NUMBER(i, j)|i:decimal digit count of effective numbers j:decimal digit count under floating-point|NUMBER: default i=38, j=0, and 22bytes.
FLOAT(i)|i:binary digit count unber floating-point|i: 1~128, default 128
BINARY_FLOAT|32bit floating-point number|4bytes
BINARY_DOUBLE|64bit floating-point number|8bytes
DATE|date|year, month, day, hour, minute, second
TIMESTAMP|date and milli-second|to milli-second
CLOB|Large OBject for string|
NCLOB|Large OBject for Unicode|
BLOB|Large OBject for Binary Data|
BFILE|File Locator|

And so on.

##### ii. Constraints
- **NOT NULL**: 칼럼에 반드시 데이터를 입력 하도록 함.  
- **UNIUQUE**: 해당 칼럼 및 칼럼들의 값 조합은 유일하도록 함.
- **PRIMARY KEY**: UNIQUE + NOT NULL
- **FOREIGN KEY**: 테이블 간의 참조 관계를 만드는 것이고, 데이터의 무결성을 위해 있으나 데이터 간 결속력이 강해져 데이터 구조의 변화가 예상될 때는 적절치 않음.
- **CHECK**:칼럼에 입력되는 데이터를 체크

<br/>

제약 조건을 포함한 Table 생성 예시
```sql
CREATE TABLE TEST_TABLE2 (
  COL1  VARCHAR2(20) DEFAULT ' ' NOT NULL,
  COL2  NUMBER,
  COL3  NUMBER(10, 5),
  COL4  VARCHAR2(30),
  COL5  VARCHAR2(30) UNIQUE NOT NULL,
  COL6  VARCHAR2(30),
  CREATE_USER_ID VARCHAR2(20),
  CREATE_TIME DATE,
  UPDATE_USER_ID VARCHAR2(20),
  UPDATE_TIME DATE,

  CONSTRAINT PK_TEST_TABLE2 PRIMARY KEY(COL6),
  CONSTRAINT UNIQUE1_TEST_TABLE2 UNIQUE(COL4),
  CONSTRAINT CHK1_TEST_TABLE2 CHECK (COL3 > 0)
);

ALTER TABLE TEST_TABLE2
ADD CONSTRAINT UNIQUE2_TEST_TABLE2 UNIQUE(COL4, COL1);


CREATE TABLE TEST_TABLE3 AS
SELECT {Statements};
```

<br/>
<div id="view"></div>

#### - <a href="#main_list">View</a>
View는 쿼리를 통해 조회되는 데이터를 마치 테이블 보는 것과 같이 할 수 있게 하는 데이터베이스 객체입니다. 뷰는 테이블 자체 및 쿼리를 감출 수 있기 때문에 보안에 있어서 좋습니다. 또, 여러개의 테이블에서 필요한 정보를 종합적으로 사용할 때 뷰를 활용하면 좋습니다.
<br/>

```sql
-- Create View
CREATE OR REPLACE VIEW TEST_VIEW AS
{SELECT STATEMENTS};


-- Delete View
DROP VIEW TEST_VIEW;
```

<br/>
<div id="index"></div>

#### - <a href="#main_list">Index</a>
인덱스는 뜻 그대로 색인. 테이블의 데이터를 빠르게 조회하기 위한 객체입니다. 한 가지 이상의 칼럼으로 인덱스를 구성할 수 있고, 여러 종류로 분류할 수 있지만 크게 Unique, Non-Unique Index로 나눌 수 있습니다.

```sql
-- Create Non-unique Index
CREATE INDEX TEST_INDEX_1
ON TEST_TABLE(COL1, COL2, COL3,...);

-- Create Unique Index
CREATE UNIQUE INDEX TEST_INDEX_2
ON TEST_TABLE(COL1, COL2, COl3,...);

-- Delete Index
DROP INDEX TEST_INDEX_2;
```

<br/>
<div id="synonym"></div>

#### - <a href="#main_list">Synonym</a>
말 그대로 동의어, 즉 별칭을 의미하며 대부분의 Oracle Object에 적용될 수 있습니다.

```sql
-- Create Synonym (Private)
CREATE OR REPLACE SYNONYM TEST_SYNONYM1
FOR {object_name};

-- Create Public Synonym
CREATE OR REPLACE PUBLIC SYNONYM TEST_SYNONYM2 
FOR {object_name};

```
<br/>
<div id="seq"></div>

#### - <a href="#main_list">Sequence</a>
시퀀스는 순서, 순번을 반환하는 객체입니다. 최솟값, 최댓값, 증감값 등을 설정할 수 있으며 순환적으로 순번을 반환하도록 구성할 수도 있습니다.

```sql
-- Create Sequence
CREATE SEQUENCE TEST_SEQUENCE
INCREMENT BY {increment_number}
START WITH {staring number}
MINVALUE (or NOMINVALUE)
MAXVALUE (or NOMAXVALUE)
NOCYCLE (or CYCLE)
NOCACHE (or CACHE);

SELECT TEST_SEQUENCE.CURRVAL, TEST_SEQUENCE.NEXTVAL FROM DUAL;

-- Delete Sequence
DROP SEQUENCE TEST_SEQUENCE;
```

<br/>
<div id="fcn"></div>

#### - <a href="#main_list">Function</a>
Function은 Oracle의 PL/SQL을 통해 지원하는 객체이며, 일반적인 함수의 역할과 동일합니다. 다만, 함수 내에서는 DML이 금지됩니다.

```sql
CREATE OR REPLACE FUNCTION TEST_FUNCTION(PARA1 TYPE1, PARA2 TYPE2, PARA3 TYPE3)
RETURN RETURN_DATA_TYPE;
  {Declaration}
IS
BEGIN
  {Execution}
  RETURN RET_VAL;
EXCEPTION

END TEST_FUNCTION;
```

<br/>
<div id="proc"></div>

#### - <a href="#main_list">Procedure</a>
Procedure도 함수 객체와 비슷하게 PL/SQL을 통해 지원되는 객체이며, DML이 허용된다는 점이 차이가 있습니다.

```sql
CREATE OR REPLACE PROCEDURE TEST_PROCEDURE (PARA1 (IN | OUT | IN OUT) TYPE1, PARA2 (IN | OUT | IN OUT) TYPE2, )

IS
  {Declaration}
BEGIN
  {Execution}
EXCEPTION

END TEST_PROCEDURE;
```

<br/>
<div id="package"></div>


#### - <a href="#main_list">Package</a>
패키지는 연관성이 있는 PL/SQL 데이터 타입 및 함수, 프로시져 등을 한 데 묶어놓은 객체입니다.

```sql
--- package head
CREATE OR REPLACE PACKAGE TEST_PACKAGE IS
  {Declaration of Variables, Funtions, and Procedures}

END TEST_PACKAGE;

--- package implementation
CREATE OR REPLACE PACKAGE BODY TEST_PACKAGE IS
  {Implementaion of Variables, Funtions, and Procedures}

END TEST_PACKAGE;
```

