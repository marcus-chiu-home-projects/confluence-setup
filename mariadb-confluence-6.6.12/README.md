server id: B6GO-NCP4-E3U3-S1BI

NOTE THE PREFIX MYSQL!!!!!!!!!!!!!!!!!!!!!!!!!!

Installation Directory: /opt/mysql-atlassian/confluence 
Home Directory: /var/mysql-atlassian/application-data/confluence 
HTTP Port: 8090 
RMI Port: 8000

- database: confluence
- username: confluenceuser
- password: password


### Confluence Installation
- chmod a+x atlassian-confluence-6.6.12-x64.bin
- sudo ./atlassian-confluence-6.6.12-x64.bin
- stop server: ./opt/mysql-atlassian/confluence/bin/stop-confluence.sh
- setup MySQL server
- start server: ./opt/mysql-atlassian/confluence/bin/start-confluence.sh

### MySQL Installation and Setup
- install MariaDb (a replacement of MySQL) via apt-get
- take mysql-connector-java-5.1.47.jar and place it into <confluence-home>/confluence/WEB-INF/lib where all the other *.jar files are
- below is to placed in my.ini (for mariadb: /etc/mysql/mariadb.conf.d/50-server.conf)
<code>
[mysql]
# below config options is for confluence server setup
# https://confluence.atlassian.com/doc/database-setup-for-mysql-128747.html
character-set-server=utf8
collation-server=utf8_bin
default-storage-engine=INNODB
max_allowed_packet=256M
innodb_log_file_size=2GB
transaction-isolation=READ-COMMITTED
binlog_format=row
// remove the line below if it exists
sql_mode = NO_AUTO_VALUE_ON_ZERO 
</code>

- commands to execute in mysql prompt
  - CREATE DATABASE confluence CHARACTER SET utf8 COLLATE utf8_bin;
  - CREATE USER 'confluenceuser'@'localhost' IDENTIFIED BY 'password';
  - GRANT ALL PRIVILEGES ON confluence.* TO 'confluenceuser'@'localhost';
  - FLUSH PRIVILEGES;
