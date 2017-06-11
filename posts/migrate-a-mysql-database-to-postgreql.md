<!-- 
.. title: Migrate a MySQL database to postgreql
.. slug: migrate-a-mysql-database-to-postgreql
.. date: 2017-06-11 20:16:24 UTC+10:00
.. tags: MySQL, postgresql, web2py, pgloader
.. category: 
.. link: 
.. description: 
.. type: text
-->

Ran into some problems using **MySQL** on **Dreamhost** as the online database manager for my **web2py PestList app**.  Decided to upgrade the database to postgresql. **DreamHost** doesn't support pg, so I had to revert to running pg on localhost.  After several attempts to convert the **MySQL** tables to **pg**, I came across **pgloader**, which did the trick.  I simply created an empty **pg** database and ran the following command.
~~~sh
$ pgloader mysql://user:pass@mysql.guaminsects.net/pestlist postgresql://user:pass/localhost/import_test
~~~