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