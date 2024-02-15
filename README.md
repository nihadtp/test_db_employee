# test_db_employee
A mysql docker with sample employee database with an integrated test suite, used to test your applications and database servers

This repository was migrated from [Launchpad](https://launchpad.net/test-db).

See usage in the [MySQL docs](https://dev.mysql.com/doc/employee/en/index.html)


## Where it comes from

The original data was created by Fusheng Wang and Carlo Zaniolo at 
Siemens Corporate Research. The data is in XML format.
http://timecenter.cs.aau.dk/software.htm

Giuseppe Maxia made the relational schema and Patrick Crews exported
the data in relational format.

The database contains about 300,000 employee records with 2.8 million 
salary entries. The export data is 167 MB, which is not huge, but
heavy enough to be non-trivial for testing.

The data was generated, and as such there are inconsistencies and subtle
problems. Rather than removing them, we decided to leave the contents
untouched, and use these issues as data cleaning exercises.

## Prerequisites

Docker 

## Installation:



Pull the image

    docker pull nihadtp/mysql:latest


Run the image with following environment variable. Make sure to set  MYSQL_DATABASE variable to  'employees'.

    docker run --name <some-name> -e MYSQL_ROOT_PASSWORD=<password> -e MYSQL_USER=<username> -e MYSQL_PASSWORD=<password> -e MYSQL_DATABASE=employees

Check the docker descktop if the container is up and running.
## Testing the installation

After container is up, you can run following

    docker exec -it <some-name> bash -c 'mysql -u <username> -p<password>'

Now you are in  mysql shell inside the container. Test the databases and tables.

    mysql> show databases;
    +--------------------+
    | Database           |
    +--------------------+
    | employees          |
    | information_schema |
    | performance_schema |
    +--------------------+
    3 rows in set (0.09 sec)
    
    mysql> USE employees
    Reading table information for completion of table and column names
    You can turn off this feature to get a quicker startup with -A
    
    Database changed
    mysql> show tables;
    +----------------------+
    | Tables_in_employees  |
    +----------------------+
    | current_dept_emp     |
    | departments          |
    | dept_emp             |
    | dept_emp_latest_date |
    | dept_manager         |
    | employees            |
    | salaries             |
    | titles               |
    +----------------------+
    8 rows in set (0.02 sec)
    
    mysql> describe salaries;
    +-----------+------+------+-----+---------+-------+
    | Field     | Type | Null | Key | Default | Extra |
    +-----------+------+------+-----+---------+-------+
    | emp_no    | int  | NO   | PRI | NULL    |       |
    | salary    | int  | NO   |     | NULL    |       |
    | from_date | date | NO   | PRI | NULL    |       |
    | to_date   | date | NO   |     | NULL    |       |
    +-----------+------+------+-----+---------+-------+
    4 rows in set (0.04 sec)


## FOR MORE OPTIONS FOR MYSQL

Visit https://hub.docker.com/_/mysql for more options assosciated with mysql docker image.

## DISCLAIMER

To the best of my knowledge, this data is fabricated and
it does not correspond to real people. 
Any similarity to existing people is purely coincidental.


## LICENSE
This work is licensed under the 
Creative Commons Attribution-Share Alike 3.0 Unported License. 
To view a copy of this license, visit 
http://creativecommons.org/licenses/by-sa/3.0/ or send a letter to 
Creative Commons, 171 Second Street, Suite 300, San Francisco, 
California, 94105, USA.


