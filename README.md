# LIS_624_2026

## Managing Software

### Steps

1) `apt search tldr`: 

2) `sudo apt install tldr`: installed

3) `tldr grep`: directory does not exist 

4) `sudo apt --purge remove tldr`: removed tldr

5) `sudo apt autoremove`: removed tldr, freed up 27.8 MB disk space

6) `sudo apt clean`: to remove cached packages

7) `sudo apt install tldr-py`: installed

8) `tldr grep`: no such command 

9) `tldr -h`

10) `sudo apt --purge remove tldr-py`: removed, freed up 42 kB

11) `apt search bsd games`

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

+--------------------+

      Database           

+--------------------+

  information_schema 

  mysql              

  performance_schema 

  sys                

+--------------------+

4 rows in set (0.02 sec)

12) `\q`: quit

13) `sudo mysql -u root`

14) `create user 'opacuser'@'localhost' identified by 'XXXXXXXXX';`: Query OK, 0 rows affected (0.03 sec)

15) `create database opacdb default character set utf8mb4 collate utf8mb4_0900_ai_ci;`: Query OK, 1 row affected (0.14 sec) 

16) `show databases;`

+--------------------+

       Database           
       
+--------------------+
 
  information_schema 
 
  mysql              
 
  opacdb             
 
  performance_schema 
 
  sys                
 
+--------------------+

5 rows in set (0.03 sec)

17) `grant all privileges on opacdb.* to 'opacuser'@'localhost';`: Query OK, 0 rows affected (0.01 sec)

18) `edit ~/.bashrc`: open edit and on end add export mysql_ps1="[\d]> "

19) `source ~/.bashrc`

20) `mysql -u opacuser -p`: to sign in 

`show databases;`

+--------------------+

       Database           

+--------------------+
 
  information_schema 
 
  opacdb             
 
  performance_schema 

+--------------------+

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

+------------------+
 
  Tables_in_opacdb 

+------------------+
 
  books            

+------------------+

1 row in set (0.01 sec)

24) `describe books;`

+-----------+--------------+------+-----+---------+----------------+

|---Field----|-----Type------|-Null-|-Key-|-Default-|-----Extra------|


+-----------+--------------+------+-----+---------+----------------+

|-id--------|-int unsigned-|-NO---|-PRI-|-NULL----|-auto_increment-|

|_author____|_varchar(150)_|_NO___|_____|_NULL____|________________|

| title     | varchar(150) | NO   |     | NULL    |                |

| copyright | year         | NO   |     | NULL    |                |

+-----------+--------------+------+-----+---------+----------------+


25) `insert into books (author, title, copyright) values

    ('Jennifer Egan', 'The Candy House', '2022'),
    
    ('Imbolo Mbue', 'How Beautiful We Were', '2021'),
    
    ('Lydia Millet', 'A Children\'s Bible', '2020'),
    
    ('Julia Phillips', 'Disappearing Earth', '2019');`

26) `select * from books;`

+----+----------------+-----------------------+-----------+
| id | author         | title                 | copyright |
+----+----------------+-----------------------+-----------+
|  1 | Jennifer Egan  | The Candy House       |      2022 |
|  2 | Imbolo Mbue    | How Beautiful We Were |      2021 |
|  3 | Lydia Millet   | A Children's Bible    |      2020 |
|  4 | Julia Phillips | Disappearing Earth    |      2019 |
+----+----------------+-----------------------+-----------+

27) `select author from books;`

+----------------+
| author         |
+----------------+
| Jennifer Egan  |
| Imbolo Mbue    |
| Lydia Millet   |
| Julia Phillips |
+----------------+

28) `select copyright from books;`

+-----------+
| copyright |
+-----------+
|      2022 |
|      2021 |
|      2020 |
|      2019 |
+-----------+

29) `select author, title from books;`

+----------------+-----------------------+
| author         | title                 |
+----------------+-----------------------+
| Jennifer Egan  | The Candy House       |
| Imbolo Mbue    | How Beautiful We Were |
| Lydia Millet   | A Children's Bible    |
| Julia Phillips | Disappearing Earth    |
+----------------+-----------------------+

30) `select author from books where author like '%millet%';`

+--------------+
| author       |
+--------------+
| Lydia Millet |
+--------------+

31) `select title from books where author like '%mbue%';`

+-----------------------+
| title                 |
+-----------------------+
| How Beautiful We Were |
+-----------------------+

32) `select author, title form books where title not like '%e%';`

      ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'books where title not like '%e%'' at line 1
      I put form instead of from

33) `select author, title from books where title not like '%e%';'
      Empty set (0.00 sec)
      I need to remove the extra % after e

34) `select author, title from books where title not like '%e';'

+----------------+--------------------+
| author         | title              |
+----------------+--------------------+
| Julia Phillips | Disappearing Earth |
+----------------+--------------------+

35) `select * from books;`

+----+----------------+-----------------------+-----------+
| id | author         | title                 | copyright |
+----+----------------+-----------------------+-----------+
|  1 | Jennifer Egan  | The Candy House       |      2022 |
|  2 | Imbolo Mbue    | How Beautiful We Were |      2021 |
|  3 | Lydia Millet   | A Children's Bible    |      2020 |
|  4 | Julia Phillips | Disappearing Earth    |      2019 |
+----+----------------+-----------------------+-----------+

36) `alter table books add publisher varchar(75) after title;`

37) `describe books;`

+-----------+--------------+------+-----+---------+----------------+
| Field     | Type         | Null | Key | Default | Extra          |
+-----------+--------------+------+-----+---------+----------------+
| id        | int unsigned | NO   | PRI | NULL    | auto_increment |
| author    | varchar(150) | NO   |     | NULL    |                |
| title     | varchar(150) | NO   |     | NULL    |                |
| publisher | varchar(75)  | YES  |     | NULL    |                |
| copyright | year         | NO   |     | NULL    |                |
+-----------+--------------+------+-----+---------+----------------+

38) `update books set publisher='Simon & Schuster' where id='1';`

39) `update books set publisher='Penguin Random House' where id='2';`

40) `update books set publisher='W. W. Norton & Company' where id='3';`

41) `update books set publisher='Knopf' where id='4';`

42) `select * from books;`

+----+----------------+-----------------------+------------------------+-----------+
| id | author         | title                 | publisher              | copyright |
+----+----------------+-----------------------+------------------------+-----------+
|  1 | Jennifer Egan  | The Candy House       | Simon & Schuster       |      2022 |
|  2 | Imbolo Mbue    | How Beautiful We Were | Penguin Random House   |      2021 |
|  3 | Lydia Millet   | A Children's Bible    | W. W. Norton & Company |      2020 |
|  4 | Julia Phillips | Disappearing Earth    | Knopf                  |      2019 |
+----+----------------+-----------------------+------------------------+-----------+

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

## Introduction to Relational Databases

### Steps

1) `sudo mysql -u root`

2) `create database DinnerDB;`

3) `show databases;`: to make sure it's there

4) `grant all privileges on DinnerDB.* to 'opacuser'@'localhost';`

5) `\q`: to exit

6) `mysql -u opacuser -p`: to sign in

7) `show databases;`

8) `use DinnerDB;`

9) `create table Meals (

    -> meal_id int auto_increment primary key,
    
    -> meal_name varchar(100) not null,
    
    -> cuisine varchar(50),
    
    -> cooking_time int not null default 1 check (cooking_time > 0),
    
    -> vegetarian boolean
    
    -> );`
    
10) `create table Ingredients (

    -> ingredient_id int auto_increment primary key,
    
    -> meal_id int not null,
    
    -> ingredient_name varchar(100) not null, 
    
    -> quantity varchar (50),
    
    -> foreign key (meal_id) references Meals(meal_id) on delete cascade
    
    -> );`
    
11) `create table Ingredients (

    -> ingredient_id int auto_increment primary key,
    
    -> meal_id int not null,
    
    -> ingredient_name varchar(100) not null, 
    
    -> quantity varchar (50),
    
    -> foreign key (meal_id) references Meals(meal_id) on delete cascade
    
    -> );`
    
12) `insert into Ingredients (meal_id, ingredient_name, quantity) values

    -> (1, 'Spaghetti', '200g'),
    
    -> (1, 'Ground Beef', '250g'),
    
    -> (1, 'Tomato Sauce', '1 cup'),
    
    -> (2, 'Broccoli', '100g'),
    
    -> (2, 'Carrots', '50g'),
    
    -> (2, 'Soy Sauce', '2T'),
    
    -> (3, 'Chicken Breast', '300g'),
    
    -> (3, 'Curry Powder', '2T'),
    
    -> (3, 'Coconut Milk', '1cup'),
    
    -> (4, 'Arborio Rive', '1 cup'),
    
    -> (4, 'Mushrooms', '1 cup'),
    
    -> (4, 'Parmesan Cheese', '1/2 cup');
                
13) `select * from Meals;`

+---------+---------------------+---------+--------------+------------+
| meal_id | meal_name           | cuisine | cooking_time | vegetarian |
+---------+---------------------+---------+--------------+------------+
|       1 | Spaghetti Bolognese | Italian |           45 |          0 |
|       2 | Vegetable Stir Fry  | Chinese |           20 |          1 |
|       3 | Chicken Curry       | Indian  |           50 |          0 |
|       4 | Mushroom Risotto    | Italian |           35 |          1 |
+---------+---------------------+---------+--------------+------------+

14) ` select * from Meals where vegetarian = true;`

+---------+--------------------+---------+--------------+------------+
| meal_id | meal_name          | cuisine | cooking_time | vegetarian |
+---------+--------------------+---------+--------------+------------+
|       2 | Vegetable Stir Fry | Chinese |           20 |          1 |
|       4 | Mushroom Risotto   | Italian |           35 |          1 |
+---------+--------------------+---------+--------------+------------+

15) `select * from Meals order by cooking_time desc;`

+---------+---------------------+---------+--------------+------------+
| meal_id | meal_name           | cuisine | cooking_time | vegetarian |
+---------+---------------------+---------+--------------+------------+
|       3 | Chicken Curry       | Indian  |           50 |          0 |
|       1 | Spaghetti Bolognese | Italian |           45 |          0 |
|       4 | Mushroom Risotto    | Italian |           35 |          1 |
|       2 | Vegetable Stir Fry  | Chinese |           20 |          1 |
+---------+---------------------+---------+--------------+------------+

16) `select * from Meals order by cooking_time asc;`

+---------+---------------------+---------+--------------+------------+
| meal_id | meal_name           | cuisine | cooking_time | vegetarian |
+---------+---------------------+---------+--------------+------------+
|       2 | Vegetable Stir Fry  | Chinese |           20 |          1 |
|       4 | Mushroom Risotto    | Italian |           35 |          1 |
|       1 | Spaghetti Bolognese | Italian |           45 |          0 |
|       3 | Chicken Curry       | Indian  |           50 |          0 |
+---------+---------------------+---------+--------------+------------+

17) `select Meals.meal_name as Meals,

    ->     Ingredients.ingredient_name as Ingredients,
    
    ->     Ingredients.quantity as Quantity
    
    ->     from Meals
    
    ->     join Ingredients on Meals.meal_id = Ingredients.meal_id;`
    
+---------------------+-----------------+----------+
| Meals               | Ingredients     | Quantity |
+---------------------+-----------------+----------+
| Spaghetti Bolognese | Spaghetti       | 200g     |
| Spaghetti Bolognese | Ground Beef     | 250g     |
| Spaghetti Bolognese | Tomato Sauce    | 1 cup    |
| Vegetable Stir Fry  | Broccoli        | 100g     |
| Vegetable Stir Fry  | Carrots         | 50g      |
| Vegetable Stir Fry  | Soy Sauce       | 2T       |
| Chicken Curry       | Chicken Breast  | 300g     |
| Chicken Curry       | Curry Powder    | 2T       |
| Chicken Curry       | Coconut Milk    | 1cup     |
| Mushroom Risotto    | Arborio Rive    | 1 cup    |
| Mushroom Risotto    | Mushrooms       | 1 cup    |
| Mushroom Risotto    | Parmesan Cheese | 1/2 cup  |
+---------------------+-----------------+----------+

18) `select ingredient_name as Ingredients,

    ->     quantity as Quantity
    
    ->     from Ingredients 
    
    ->     where meal_id = (select meal_id from Meals where meal_name = 'Chicken Curry');`
    
+----------------+----------+
| Ingredients    | Quantity |
+----------------+----------+
| Chicken Breast | 300g     |
| Curry Powder   | 2T       |
| Coconut Milk   | 1cup     |
+----------------+----------+

19) `select cuisine, Count(*) as meal_count

    -> from Meals
    
    -> group by cuisine;`
    
+---------+------------+
| cuisine | meal_count |
+---------+------------+
| Italian |          2 |
| Chinese |          1 |
| Indian  |          1 |
+---------+------------+

20) `select meal_name, cooking_time 

    ->     from Meals 
    
    ->     where cooking_time <= 45
    
    ->     order by cooking_time asc;`
    
+---------------------+--------------+
| meal_name           | cooking_time |
+---------------------+--------------+
| Vegetable Stir Fry  |           20 |
| Mushroom Risotto    |           35 |
| Spaghetti Bolognese |           45 |
+---------------------+--------------+

21) `\q`

22) `sudo mysql -u root`

23) `show grants for 'opacuser'@'localhost';`

+----------------------------------------------------------------+
| Grants for opacuser@localhost                                  |
+----------------------------------------------------------------+
| GRANT USAGE ON *.* TO `opacuser`@`localhost`                   |
| GRANT ALL PRIVILEGES ON `DinnerDB`.* TO `opacuser`@`localhost` |
| GRANT ALL PRIVILEGES ON `opacdb`.* TO `opacuser`@`localhost`   |
+----------------------------------------------------------------+

24) `\q`

## Creating a Bare Bones OPAC

### Steps

1) `mysql -u opacuser -p`

2) `use opacdb;`

3) `alter table books add publication_date date;`

4) `update books set publication_date = str_to_date(concat(copyright, '-01-01'), '%Y-%m-%d');`

5) `alter table books drop column copyright;`

6) `alter table books change publication_date copyright date not null;`

7) `\q`

8) `cd /var/www/html/`

9) `sudo edit mylibrary.html`: input code

10) `sudo edit search.php`: input code

11) `mysql -u opacuser -p`

12) `use opacdb;`

13) `show tables;`

+------------------+
| Tables_in_opacdb |
+------------------+
| books            |
+------------------+

14) `select * from books;`

+----+-----------------------+-------------------------------------------+---------------------------+------------+
| id | author                | title                                     | publisher                 | copyright  |
+----+-----------------------+-------------------------------------------+---------------------------+------------+
|  1 | Jennifer Egan         | The Candy House                           | Simon & Schuster          | 2022-01-01 |
|  2 | Imbolo Mbue           | How Beautiful We Were                     | Penguin Random House      | 2021-01-01 |
|  3 | Lydia Millet          | A Children's Bible                        | W. W. Norton & Company    | 2020-01-01 |
|  5 | Chris Harris          | My Head Has A Bellyache And More Nonsense | Little, Brown And Cpmpany | 2023-01-01 |
|  6 | Emily Winfield Martin | The Wonderful Things You Will Be          | Random House              | 2025-01-01 |
|  7 | Dav Pilkey            | Dog Man Big Jim Believes                  | Scholastic Inc.           | 2025-01-01 |
+----+-----------------------+-------------------------------------------+---------------------------+------------+

15) `insert into books

    -> (author, title, publisher, copyright) values
    
    -> ('Emma Donoghue', 'Room', 'Little, Brown & Company', '2010-01-01'),
    
    -> ('Zadie Smith', 'White Teeth', 'Hamish Hamilton', '2000-01-01');`
    
16) `select * from books;`

+----+-----------------------+-------------------------------------------+---------------------------+------------+
| id | author                | title                                     | publisher                 | copyright  |
+----+-----------------------+-------------------------------------------+---------------------------+------------+
|  1 | Jennifer Egan         | The Candy House                           | Simon & Schuster          | 2022-01-01 |
|  2 | Imbolo Mbue           | How Beautiful We Were                     | Penguin Random House      | 2021-01-01 |
|  3 | Lydia Millet          | A Children's Bible                        | W. W. Norton & Company    | 2020-01-01 |
|  5 | Chris Harris          | My Head Has A Bellyache And More Nonsense | Little, Brown And Cpmpany | 2023-01-01 |
|  6 | Emily Winfield Martin | The Wonderful Things You Will Be          | Random House              | 2025-01-01 |
|  7 | Dav Pilkey            | Dog Man Big Jim Believes                  | Scholastic Inc.           | 2025-01-01 |
|  8 | Emma Donoghue         | Room                                      | Little, Brown & Company   | 2010-01-01 |
|  9 | Zadie Smith           | White Teeth                               | Hamish Hamilton           | 2000-01-01 |
| 10 | Emma Donoghue         | Room                                      | Little, Brown & Company   | 2010-01-01 |
| 11 | Zadie Smith           | White Teeth                               | Hamish Hamilton           | 2000-01-01 |
+----+-----------------------+-------------------------------------------+---------------------------+------------+

17) `delete from books where author='zadie smith';` : accidentally entered the information twice
so I wanted to delete the duplicates.

18) `delete from books where author='emma donoghue';`

19) `insert into books

     -> (author, title, publisher, copyright) values
     
     -> ('Emma Donoghue', 'Room', 'Little, Brown & Company', '2010-01-01'),
     
     -> ('Zadie Smith', 'White Teeth', 'Hamish Hamilton', '2000-01-01');`

20) `select * from books;`

+----+-----------------------+-------------------------------------------+---------------------------+------------+
| id | author                | title                                     | publisher                 | copyright  |
+----+-----------------------+-------------------------------------------+---------------------------+------------+
|  1 | Jennifer Egan         | The Candy House                           | Simon & Schuster          | 2022-01-01 |
|  2 | Imbolo Mbue           | How Beautiful We Were                     | Penguin Random House      | 2021-01-01 |
|  3 | Lydia Millet          | A Children's Bible                        | W. W. Norton & Company    | 2020-01-01 |
|  5 | Chris Harris          | My Head Has A Bellyache And More Nonsense | Little, Brown And Cpmpany | 2023-01-01 |
|  6 | Emily Winfield Martin | The Wonderful Things You Will Be          | Random House              | 2025-01-01 |
|  7 | Dav Pilkey            | Dog Man Big Jim Believes                  | Scholastic Inc.           | 2025-01-01 |
| 12 | Emma Donoghue         | Room                                      | Little, Brown & Company   | 2010-01-01 |
| 13 | Zadie Smith           | White Teeth                               | Hamish Hamilton           | 2000-01-01 |
+----+-----------------------+-------------------------------------------+---------------------------+------------+ 

## Creating a Bare Bones Cataloging Module

### Steps

1) `cd /var/www/html`

2) `sudo mkdir cataloging`

3) `cd cataloging`

4) `sudo edit index.html`: input code

5) `sudo edit insert.php`: input code

6) `sudo htpasswd -c /etc/apache2/.htpasswd libcat`

7) `sudo edit /etc/apache2/apache2.conf`: insert cataloging

8) `sudo edit .htaccess`: input code

9) `sudo apachectl configtest`

10) `sudo systemctl restart apache2`

11) `sudo systemctl status apache2`: active

12) `sudo chown :www-data /var/www/html`

13) `sudo find /var/www/html -type d -exec chmod g+s {} +`


