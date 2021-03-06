##### Backup/restore:

- Backup DB to .sql: 

```
mysqldump --routines --triggers -u root -p indb > indb.sql
```

- Restore DB from .sql file:

```
mysql -u root -p indb < indb.sql
```

- Backup DB to gzipped file	:

```
mysqldump --routines --triggers -u root -p indb | gzip > indb.sql.gz
```

- Restore DB from gzipped file:

```
zcat indb.sql.gz | mysql -u root -p
zcat indb.sql.gz | sed -e "s/\`indb\`/\`indb_psali\`/" | mysql -u root -p
```

- Backup 1 DB table to gzipped file:

```
mysqldump --routines --triggers -u root -p indb sop | gzip > indb_sop.sql.gz
```

---

##### To export privileges from MySQL:

- in bash:

```
mygrants()
{
  mysql -B -N $@ -e "SELECT DISTINCT CONCAT(
    'SHOW GRANTS FOR \'', user, '\'@\'', host, '\';'
    ) AS query FROM mysql.user" | \
  mysql $@ | \
  sed 's/\(GRANT .*\)/\1;/;s/^\(Grants for .*\)/## \1 ##/;/##/{x;p;x;}'
}
```

- dump to a privs file:

```
mygrants -u root -p > privs.sql && reset
```

- restore the sql:

```
cat privs.sql | mysql -u root -p
```
or

```
mysql -u root -p < privs.sql
```

---

##### 2 ways to connect to `mysqld` server:

- using a Unix socket file (default `/tmp/mysql.sock`):
	- with the special host name `localhost`
	- only on the same computer
	- faster than TCP/IP

- using TCP/IP network socket (default port 3306)
	- 127.0.0.1 != `localhost`
	- MySQL will not auto-resolve the host name `localhost` in `/etc/hosts` to 127.0.0.1





