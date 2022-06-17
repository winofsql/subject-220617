### インスタント クライアント

- ### [ダウンロードページ](https://www.oracle.com/database/technologies/instant-client/downloads.html)
  ![image](https://user-images.githubusercontent.com/1501327/174200802-d5c9d1e6-4796-49d4-bb7a-97b3a6cd7bb4.png)
  - 32ビットのインストール\
  ![image](https://user-images.githubusercontent.com/1501327/174201016-5f978ef0-821c-47ab-aa8a-5e784129fc11.png)\
  ![image](https://user-images.githubusercontent.com/1501327/174201505-e653becc-5d7f-4ec2-ac09-2ccc31ae3b91.png)
    - instantclient-basic-nt-21.6.0.0.0dbru.zip
    - instantclient-odbc-nt-21.6.0.0.0dbru.zip
    - 上記書庫を解凍して、中のフォルダを合体させて、c:\app\lightbox の中に作成
      - c:\app\lightbox\instantclient_21_6\
      ![image](https://user-images.githubusercontent.com/1501327/174203131-37bcb9a4-b340-490c-8df4-4006d325ea64.png)\
      ![image](https://user-images.githubusercontent.com/1501327/174204328-e414f631-3fe2-42bf-bdb3-fb8b47ff0597.png)\
      ![image](https://user-images.githubusercontent.com/1501327/174204435-97f38a2e-340b-4505-8856-2cfa6be94779.png)\
      ![image](https://user-images.githubusercontent.com/1501327/174204800-0224503c-336b-4125-95e3-7ad6e36b1d63.png)\
      ![image](https://user-images.githubusercontent.com/1501327/174205055-c2af03bd-e26a-4ed7-98dc-6374e745846a.png)

```sql
alter session set container = XEPDB1
```
```sql
create tablespace LIGHTBOX99_SPACE
	datafile 'C:\app\lightbox\product\21c\oradata\XE\LIGHTBOX99PDB.DBF'
	size 5M
	autoextend on
	next 1M
	maxsize unlimited
	segment space management AUTO;

create user LIGHTBOX99
	identified by trustno1
	default tablespace LIGHTBOX99_SPACE
	temporary tablespace TEMP
	quota unlimited on LIGHTBOX99_SPACE
	account UNLOCK;
	
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
to LIGHTBOX99	
```

https://www.dbsheetclient.jp/blog/?p=1566
https://docs.oracle.com/cd/E57425_01/121/SQPUG/GUID-E26A730D-C5B1-4CB3-BB2F-07E526B547C0.htm
