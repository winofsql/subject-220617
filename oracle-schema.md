### 各 PC 用のテーブルスペース作成
```sql
create tablespace LIGHTBOX00_SPACE
	datafile 'C:\app\lightbox\product\21c\oradata\XE\LIGHTBOX00.DBF'
	size 5M
	autoextend on
	next 1M
	maxsize unlimited
	segment space management AUTO
```

### 各ユーザの作成
```sql
create user LIGHTBOX00
	identified by trustno1
	default tablespace LIGHTBOX00_SPACE
	temporary tablespace TEMP
	quota unlimited on LIGHTBOX00_SPACE
	account UNLOCK
```

### ユーザ権限の設定
```sql
grant 
	 ALTER PROFILE
	,ALTER SESSION
	,ALTER SYSTEM
	,ALTER TABLESPACE
	,ALTER USER
	,CREATE ANY DIRECTORY
	,CREATE PROCEDURE
	,CREATE PROFILE
	,CREATE PUBLIC SYNONYM
	,CREATE ROLE
	,CREATE ROLLBACK SEGMENT
	,CREATE SEQUENCE
	,CREATE SESSION
	,CREATE SYNONYM
	,CREATE TABLE
	,CREATE TABLESPACE
	,CREATE TRIGGER
	,CREATE VIEW
	,DROP ANY DIRECTORY
	,EXECUTE ANY PROCEDURE
	,SELECT ANY DICTIONARY
	,SELECT ANY SEQUENCE
	,SELECT ANY TABLE
to LIGHTBOX00
```
