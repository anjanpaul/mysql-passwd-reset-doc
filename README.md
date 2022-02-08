## Reset MySQL root password

Use the following steps to reset MySQL root password by using the command line interface.

### Step 1: Prerequisites

You must have (Linux) root or (Windows) Administrator access to the Cloud Server to reset the MySQL root password.

Step 2: Stop MySQL Service

```
service mariadb stop

```
### Step 3: Start MySQL in Safe Mode
Run the following command. Do not forget to put ampersand (&) at the end of the command.

```
sudo mysqld_safe --skip-grant-tables &

```

### Step 4: Connect to MySQL

```
mysql -u root

```

### Step 5: Set a new MySQL root password

```
MariaDB [(none)]> use mysql;

Database changed
MariaDB [mysql]> update user set authentication_string=PASSWORD("root@123$") where User='root';

MariaDB [mysql]> flush privileges;

MariaDB [mysql]> quit

```

### Step 6: Stop and start the MySQL service

```
Stop mariadb service

```

Start mariadb service

```
service mariadb start

```

### Step 7: Log in to the database

Test the new password by logging in to the database.

```
mysql -u root -p

```