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
- confirmed PostgresSQL server set to local connections only
- added .htaccess file to /var/www to prevent accessing .git folder through browser

### Users
- added superuser `grader` to server's users
- added user `catalog` to PostgresSQL to be used by web app
    - note: if the grader needs to login to psql as catalog, use the command `psql -U catalog -h 127.0.0.1 -d readinglist`. The password can be found by viewing the file /var/www/ItemCatalogProject/views.py and looking in the connection detail in the create_engine call in line 22
