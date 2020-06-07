#Replication setup 


### To verify config on server (both master and slave)

` cat /etc/mysql/mysql.conf.d/mysqld.cnf `
	
###Master	
	
~~~~
server-id               = 1 
log_bin                 = /var/log/mysql/mysql-bin.log 
expire_logs_days        = 10 
max_binlog_size         = 100M 
binlog_do_db            = newdatabase
~~~~


###	Slave

~~~~
server-id		= 2
relay-log               = /var/log/mysql/mysql-relay-bin.log
log_bin			= /var/log/mysql/mysql-bin.log
expire_logs_days	= 10
max_binlog_size         = 100M
binlog_do_db		= newdatabase
~~~~

### Error log is available here:
log_error = /var/log/mysql/error.log

### Config file:
/etc/mysql/mysql.conf.d/mysqld.cnf

### Log bin
/var/log/mysql/mysql-bin.log

### Useful commands:
SHOW DATABASES; <br />
USE <db_name>; <br />
log_bin                 = /var/log/mysql/mysql-bin.log

### Lock database in order to record  position:
FLUSH TABLES WITH READ LOCK; <br />
SHOW MASTER STATUS;< <br />

~~~~
mysql> SHOW MASTER STATUS;
+------------------+----------+--------------+------------------+
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB |
+------------------+----------+--------------+------------------+
| mysql-bin.000001 |      107 | newdatabase  |                  |
+------------------+----------+--------------+------------------+
1 row in set (0.00 sec)
~~~~





