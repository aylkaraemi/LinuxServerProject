# Linux Server Project
A Project for the Udacity Full Stack Nanodegree

This project is a test of setting up and configuring a Linux server and deploying a web app on it.

### Server Details
- IP Address: 35.169.169.18
- SSH Port: 2200
- URL for Web App: 35.169.169.18.xip.io/ <- _must use this to login, google login will not work with just the IP address_

### Software Installed
- Apache2
- mod_wsgi
- PostgreSQL
- Git
- aptitude
- Flask Python library
- SQLAlchemy Python library
- Oauth2client Python library
- psycopg2 Python module
- Requests Python library


### Configuration changes
- Firewall configured to only allow ports 2200, 80 and 123
- Configured server to only allow public key authentication for logins
- remote login to root disabled both via `sshd_config` file (PermitRootLogin set to no) and adding `-:root:ALL EXCEPT LOCAL` to the `/etc/security/access.conf` file.
- added grader file to `/etc/sudoers.d` to allow grader to use `sudo` without entering password
- set local timezone to UTC
- confirmed PostgresSQL server set to local connections only (per PostgresSQL docs this is the default setting)
- added .htaccess file to /var/www to prevent accessing .git folder through browser

### Users
- added superuser `grader` to server's users
- added user `catalog` to PostgresSQL to be used by web app
    - note: if the grader needs to login to psql as catalog, use the command `psql -U catalog -h 127.0.0.1 -d readinglist`. The password can be found by viewing the file /var/www/ItemCatalogProject/views.py and looking in the connection detail in the create_engine call in line 22
    
### Tutorials & Documentation used:
- [Deploying Python Flask Web App on Amazon Lightsail](https://umar-yusuf.blogspot.com/2018/02/deploying-python-flask-web-app-on.html)
- [SQLAlchemy Docs - Engine Configuration](https://docs.sqlalchemy.org/en/rel_1_2/core/engines.html)
- [Serverfault - getting MOTD to disappear after upgrading all packages](https://serverfault.com/questions/262751/update-ubuntu-10-04/262773#262773)
- [Disabling Remote Root Login](https://websiteforstudents.com/how-to-disable-remote-logon-for-root-on-ubuntu-16-04-lts-servers/)
- [Stackoverflow - logging into psql without peer authentication - used for setting up catalog user, scroll down to the answer with 143 rep for what I did](https://stackoverflow.com/questions/18664074/getting-error-peer-authentication-failed-for-user-postgres-when-trying-to-ge)
- [Stackoverflow - setting up .htaccess file to prevent .git access](https://stackoverflow.com/questions/6142437/make-git-directory-web-inaccessible)
- [askUbuntu - Setting up passwordless sudo](https://askubuntu.com/questions/192050/how-to-run-sudo-command-with-no-password)
- [askUbuntu - Changing timezone to UTC](https://askubuntu.com/questions/138423/how-do-i-change-my-timezone-to-utc-gmt)
- Documentation for the python modules listed above to confirm the correct package name to use with pip
- Documentation for Git and aptitude to confirm correct package name for use with apt-get
