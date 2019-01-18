# Oracle VS MySql

> MySql is multiple database
>
> Oracle is multiple **tablespace**

# Basic Flow chart

## create tablespace

```sql
create tablespace ERP_TS
datafile 'E:\oracle-data\ts\erp.dbf'
size 100M
autoextend on
next 10M;
```

## create user and grant privilege

```sql
create user erpuser
identified by itcast
default tablespace ERP_TS;

grant dba to erpuser;
```

## create table  and other DML

`SQL> @ D:\erp.sql`

```sql
CREATE TABLE EMP  (
   UUID                 NUMBER                          NOT NULL,
   USERNAME             VARCHAR2(15),
   PWD                  VARCHAR2(32),
   NAME                 VARCHAR2(28),
   GENDER               NUMBER,
   EMAIL                VARCHAR2(255),
   TELE                 VARCHAR2(30),
   ADDRESS              VARCHAR2(255),
   BIRTHDAY             DATE,
   DEPUUID              NUMBER,
   CONSTRAINT PK_EMP PRIMARY KEY (UUID)
);

COMMENT ON TABLE EMP IS
'员工';

COMMENT ON COLUMN EMP.UUID IS
'编号';
```

create sequences

> **oracle's primary key doesn't have *auto increment* policy**

```sql
CREATE SEQUENCE  "EMP_SEQ"  NOCACHE ;
```

## Delete user and tablespace

> note: user **sys**

### basic query

```sql
-- query current user's default tablespace's tables
select * from tab;
-- query users
select * from dba_users;
-- query namespace
select * from dba_data_files;
```



```sql
-- 级联删除用户
drop user erpuser cascade;
-- 级联删除tablespace
drop tablespace erp_ts including contents and datafiles cascade constraint;
```

