# WBY Docker Base Image for MySQL5.6

Github: https://github.com/kissjared/docker-mysql-base.git

## To Build

``` bash
$ docker build -t docker-mysql-base .
Sending build context to Docker daemon   51.2kB
Step 1/7 : FROM mysql:5.6
 ---> cdfa8cc50c33
Step 2/7 : MAINTAINER weiboyi lijie1@weiboyi.com
 ---> Using cache
 ---> 4da8f2048d88
Step 3/7 : COPY ./devbox.cnf /etc/mysql/mysql.conf.d/
 ---> Using cache
 ---> 486edfda2bce
Step 4/7 : VOLUME /var/lib/mysql
 ---> Using cache
 ---> 700b4fa90a36
Step 5/7 : ENTRYPOINT docker-entrypoint.sh
 ---> Using cache
 ---> 2b881491f0b1
Step 6/7 : EXPOSE 3306
 ---> Using cache
 ---> 2307edd6e8a1
Step 7/7 : CMD mysqld
 ---> Using cache
 ---> 71e95a7025d8
Successfully built 71e95a7025d8
Successfully tagged docker-mysql-base:latest
```

## To Run

Use [docker volumes](http://docs.docker.io/use/working_with_volumes/) to expose

``` bash
$ docker run --name my-test-db -v /opt/mydb_dir:/var/lib/mysql -e MYSQL_ROOT_PASSWORD='root' -d docker-mysql-base
eaaa771656355ae331915fead5070d959168f517ba233af6720d39071ffb5e88

$ docker exec -it eaaa77165635 bash
root@eaaa77165635:/# mysql -uroot -proot
Warning: Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.6.37-log MySQL Community Server (GPL)

Copyright (c) 2000, 2017, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
+--------------------+
3 rows in set (0.01 sec)
```
