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
