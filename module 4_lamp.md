## Installing the Apache Web Server

### Steps


1) `apt search apache2 | head`

2) `apt show apache2`

3) `cd /var/`: now in var directory 

4) `ls`: backups  cache  crash  lib  local  lock  log  mail  opt  run  snap  spool  tmp

5) `sudo apt install apache2`

6) `ls`: backups  cache  crash  lib  local  lock  log  mail  opt  run  snap  spool  tmp  www

7) `systemctl status apache2`: active

8) `sudo apt install elinks`

9) `elinks 127.0.0.1`: It works

10) `ip a`

11) `elinks http://10.128.0.3`: It works

12) `cd /www/html`: -bash: cd: /www/html: No such file or directory, I forgot to put
    /var in front

13) `cd /var/www/html/`: jessieloso@spring-2026-jvargo:/var/www/html$ 

14) `ls`: index.html

15) `sudo mv index.html index.orginal.html`

16) `ls`: index.original.html

17) `sudo edit index.html`: opens edit and insert text.
When I refreshed page it said URL not found. I realized that I needed to save the
changes in edit then reload the page. When I refreshed it says Welcome

## Installing and Configuring PHP

### Steps

1) `apt show php`

2) `sudo apt install php libapache2-mod-php`

3) `sudo systemctl restart apache2`

4) `php -v`

5) `systemctl status apache2`: active

6) `cd /var/www/html/`: jessieloso@spring-2026-jvargo:/var/www/html$

7) `ls`: index.html  index.original.html

8) `sudo edit info.php`: open edit

9) `sudo rm /var/www/html/info.php`: removes file

10) `cd /etc/apache2/mods-available/`: jessieloso@spring-2026-jvargo:/etc/apache2/mods-available$

11) `ls`: list of mods available

12) `sudo cp dir.conf dir.conf.bak`: added backup

13) `sudo eidt dir.conf`: opens directory index in edit
insert index.php at the front and remove later listing.

14) `apachectl configtest`: syntax OK

15) `sudo systemctl reload apache2`: reloads system

16) `systemctl status apache2` : active

17) `cd /var/www/html/`: goes to the document root

18) `ls`: index.html  index.original.html

19) `sudo edit index.php`: File opened insert text


## Installing and Configuring MySQL

### Steps
1) `sudo apt update` 

2) `sudo upgrade`: sudo: upgrade: command not found
Forgot to put in apt

3) `sudo apt upgrage`

4) `sudo apt autoremove`

5) `sudo apt clean`

6) `sudo apt install mysql-server`: installed

7) `apt policy mysql-server`: mysql-server:
   
8) `mysql --version`

9) `systemctl status mysql`: active 

10) `sudo mysql_secure_installation`

11) `sudo mysql -u root`

`show databaes;`

```
+--------------------+
|     Database       |    
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                | 
+--------------------+
```

12) `\q`: quit

13) `sudo mysql -u root`

14) `create user 'opacuser'@'localhost' identified by 'XXXXXXXXX';`: Query OK, 0 rows affected (0.03 sec)

15) `create database opacdb default character set utf8mb4 collate utf8mb4_0900_ai_ci;`: Query OK, 1 row affected (0.14 sec) 

16) `show databases;`

```
+--------------------+
|      Database      |           
+--------------------+ 
| information_schema | 
| mysql              | 
| opacdb             |   
| performance_schema |  
| sys                |  
+--------------------+
```

5 rows in set (0.03 sec)

17) `grant all privileges on opacdb.* to 'opacuser'@'localhost';`: Query OK, 0 rows affected (0.01 sec)

18) `edit ~/.bashrc`: open edit and on end add export mysql_ps1="[\d]> "

19) `source ~/.bashrc`

20) `mysql -u opacuser -p`: to sign in 

`show databases;`

```
+--------------------+
|      Database      |     
+--------------------+
| information_schema |
| opacdb             |
| performance_schema |
+--------------------+
```

3 rows in set (0.06 sec)

21) `use opacdb;`: Database changed

22) `create table books (
        id int unsigned not null auto_increment,
        author varchar(150) not null,
        title varchar(150) not null,
        copyright year not null,
        primary key (id)
);`: Query OK, 0 rows affected (0.12 sec)

23) `show tables;`

```
+------------------+
| Tables_in_opacdb |
+------------------+
| books            |
+------------------+
```

24) `describe books;`

```
+-----------+--------------+------+-----+---------+----------------+
|   Field   |     Type     | Null | Key | Default |     Extra      |
+-----------+--------------+------+-----+---------+----------------+
| id        | int unsigned | NO   | PRI | NULL    | auto_increment |
| author    | varchar(150) | NO   |     | NULL    |                |
| title     | varchar(150) | NO   |     | NULL    |                |
| copyright | year         | NO   |     | NULL    |                |
+-----------+--------------+------+-----+---------+----------------+
```

25) `insert into books (author, title, copyright) values

    ('Jennifer Egan', 'The Candy House', '2022'),
    
    ('Imbolo Mbue', 'How Beautiful We Were', '2021'),
    
    ('Lydia Millet', 'A Children\'s Bible', '2020'),
    
    ('Julia Phillips', 'Disappearing Earth', '2019');`

26) `select * from books;`

```
+----+----------------+-----------------------+-----------+
| id | author         | title                 | copyright |
+----+----------------+-----------------------+-----------+
|  1 | Jennifer Egan  | The Candy House       |      2022 |
|  2 | Imbolo Mbue    | How Beautiful We Were |      2021 |
|  3 | Lydia Millet   | A Children's Bible    |      2020 |
|  4 | Julia Phillips | Disappearing Earth    |      2019 |
+----+----------------+-----------------------+-----------+
```

27) `select author from books;`

```
+----------------+
| author         |
+----------------+
| Jennifer Egan  |
| Imbolo Mbue    |
| Lydia Millet   |
| Julia Phillips |
+----------------+
```

28) `select copyright from books;`

```
+-----------+
| copyright |
+-----------+
|      2022 |
|      2021 |
|      2020 |
|      2019 |
+-----------+
```

29) `select author, title from books;`

```
+----------------+-----------------------+
| author         | title                 |
+----------------+-----------------------+
| Jennifer Egan  | The Candy House       |
| Imbolo Mbue    | How Beautiful We Were |
| Lydia Millet   | A Children's Bible    |
| Julia Phillips | Disappearing Earth    |
+----------------+-----------------------+
```

30) `select author from books where author like '%millet%';`

```
+--------------+
| author       |
+--------------+
| Lydia Millet |
+--------------+
```

31) `select title from books where author like '%mbue%';`

```
+-----------------------+
| title                 |
+-----------------------+
| How Beautiful We Were |
+-----------------------+
```

32) `select author, title form books where title not like '%e%';`

      ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'books where title not like '%e%'' at line 1
      I put form instead of from

33) `select author, title from books where title not like '%e%';'
      Empty set (0.00 sec)
      I need to remove the extra % after e

34) `select author, title from books where title not like '%e';'

```
+----------------+--------------------+
| author         | title              |
+----------------+--------------------+
| Julia Phillips | Disappearing Earth |
+----------------+--------------------+
```

35) `select * from books;`

```
+----+----------------+-----------------------+-----------+
| id | author         | title                 | copyright |
+----+----------------+-----------------------+-----------+
|  1 | Jennifer Egan  | The Candy House       |      2022 |
|  2 | Imbolo Mbue    | How Beautiful We Were |      2021 |
|  3 | Lydia Millet   | A Children's Bible    |      2020 |
|  4 | Julia Phillips | Disappearing Earth    |      2019 |
+----+----------------+-----------------------+-----------+
```

36) `alter table books add publisher varchar(75) after title;`

37) `describe books;`

```
+-----------+--------------+------+-----+---------+----------------+
| Field     | Type         | Null | Key | Default | Extra          |
+-----------+--------------+------+-----+---------+----------------+
| id        | int unsigned | NO   | PRI | NULL    | auto_increment |
| author    | varchar(150) | NO   |     | NULL    |                |
| title     | varchar(150) | NO   |     | NULL    |                |
| publisher | varchar(75)  | YES  |     | NULL    |                |
| copyright | year         | NO   |     | NULL    |                |
+-----------+--------------+------+-----+---------+----------------+
```

38) `update books set publisher='Simon & Schuster' where id='1';`

39) `update books set publisher='Penguin Random House' where id='2';`

40) `update books set publisher='W. W. Norton & Company' where id='3';`

41) `update books set publisher='Knopf' where id='4';`

42) `select * from books;`

```
+----+----------------+-----------------------+------------------------+-----------+
| id | author         | title                 | publisher              | copyright |
+----+----------------+-----------------------+------------------------+-----------+
|  1 | Jennifer Egan  | The Candy House       | Simon & Schuster       |      2022 |
|  2 | Imbolo Mbue    | How Beautiful We Were | Penguin Random House   |      2021 |
|  3 | Lydia Millet   | A Children's Bible    | W. W. Norton & Company |      2020 |
|  4 | Julia Phillips | Disappearing Earth    | Knopf                  |      2019 |
+----+----------------+-----------------------+------------------------+-----------+
```

43) `delete from books where author='Julia Phillips';`


44) `insert into books

    (author, title, publisher, copyright) values
    
    ('Chris Harris', 'My Head Has A Bellyache And More Nonsense', 'Little, Brown And Company', '2023'),
    
    ('Emily Winfield Martin', 'The Wonderful Things You Will Be', 'Random House', '2015'),
    
    ('Dav Pilkey', 'Dog Man Big Jim Believes', 'Scholastic Inc.', '2025');`
    
        I got an error, not sure why so I tried to add one book to see if it would work

45) `insert into books (author, title, publisher, copyright) values 
    
    ('Chris Harris', 'My Head Has A Bellyache And More Nonsense', 'Little, Brown And Cpmpany', '2023');`

      This worked not sure what happened.

46) `insert into books (author, title, publisher, copyright) values

    -> ('Emily Winfield Martin', 'The Wonderful Things You Will Be', 'Random House', '2025'),
    
    -> ('Dav Pilkey', 'Dog Man Big Jim Believes', 'Scholastic Inc.', '2025');`
    
      I was able to add two books at once so I'm not sure why the first one didn't work.

47) `select * from books;`

```
+----+-----------------------+-------------------------------------------+---------------------------+-----------+
| id | author                | title                                     | publisher                 | copyright |
+----+-----------------------+-------------------------------------------+---------------------------+-----------+
|  1 | Jennifer Egan         | The Candy House                           | Simon & Schuster          |      2022 |
|  2 | Imbolo Mbue           | How Beautiful We Were                     | Penguin Random House      |      2021 |
|  3 | Lydia Millet          | A Children's Bible                        | W. W. Norton & Company    |      2020 |
|  5 | Chris Harris          | My Head Has A Bellyache And More Nonsense | Little, Brown And Cpmpany |      2023 |
|  6 | Emily Winfield Martin | The Wonderful Things You Will Be          | Random House              |      2025 |
|  7 | Dav Pilkey            | Dog Man Big Jim Believes                  | Scholastic Inc.           |      2025 |
+----+-----------------------+-------------------------------------------+---------------------------+-----------+
```

48) `sudo apt install php-mysql`

49) `sudo systemctl restart apache2`

50) `sudo systemctl restart mysql`

51) `cd /var/www`

52) `sudo touch login.php`

53) `sudo chmod 640 login.php`

54) `ls -l login.php`

55) `sudo chown :www-data login.php`

56) `ls -l`

57) `sudo edit login.php`: input code

58) `cd /var/www/html`

59) `sudo edit opac.php`: input code

60) `sudo php -f /var/www/login.php`

61) `sudo php -f var/www/html/opac.php`: error couldn't open file opac.php
  
      took a while to figure our that I forgot a / in front of var

62) `sudo php -f /var/www/html/opac.php`

63) `cat ../login.php`

64) `sudo cat ../login.php`

### Issues Encountered:

- `sudo upgrade`: sudo: upgrade: command not found
I forgot to put in apt 

- `select author, title from books where title not like '%e%';`: Empty set 
I need to remove the extra % after e

- `insert into books
(author, title, publisher, copyright) values
('Chris Harris', 'My Head Has A Bellyache And More Nonsense', 'Little, Brown And Company', '2023'),
('Emily Winfield Martin', 'The Wonderful Things You Will Be', 'Random House', '2015'),
('Dav Pilkey', 'Dog Man Big Jim Believes', 'Scholastic Inc.', '2025');`
I got an error, not sure why so I tried to add one book to see if it would work.
Adding one book worked. So I tried again with two books and it worked so I'm not sure why
my first command didn't work.

- `sudo php -f var/www/html/opac.php`: error couldn't open file opac.php
took a while to figure our that I forgot a / in front of var

### What I learned:

It is very important to ensure that everything is typed correctly. I am still not sure what
happended when I tried to add multiple books the first time. I learned how to install MySQL. 
I created a table and was able to search it for information. I also added to the table. I was 
able to pull specific data to my website.  

