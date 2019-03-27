server id: B6GO-NCP4-E3U3-S1BI

Installation Directory: /opt/atlassian/confluence 
Home Directory: /var/atlassian/application-data/confluence 
HTTP Port: 8090 
RMI Port: 8000


database: confluence
user: confluenceuser
password: password

### Install Postgres & Setup User and Database
- https://confluence.atlassian.com/doc/database-setup-for-postgresql-173244522.html
- sudo apt-get install postgresql postgresql-contrib
- sudo -u postgres psql
- CREATE USER confluenceuser WITH PASSWORD 'password';
- CREATE DATABASE confluence ENCODING 'UTF8' LC_COLLATE = 'en_US.UTF-8' LC_CTYPE = 'en_US.UTF-8' TEMPLATE template0;
- grant all privileges on database confluence to confluenceuser;
