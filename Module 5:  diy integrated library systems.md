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
    
    -> (4, 'Parmesan Cheese', '1/2 cup');`
                
13) `select * from Meals;`

```
+---------+---------------------+---------+--------------+------------+
| meal_id | meal_name           | cuisine | cooking_time | vegetarian |
+---------+---------------------+---------+--------------+------------+
|       1 | Spaghetti Bolognese | Italian |           45 |          0 |
|       2 | Vegetable Stir Fry  | Chinese |           20 |          1 |
|       3 | Chicken Curry       | Indian  |           50 |          0 |
|       4 | Mushroom Risotto    | Italian |           35 |          1 |
+---------+---------------------+---------+--------------+------------+
```

14) ` select * from Meals where vegetarian = true;`

```
+---------+--------------------+---------+--------------+------------+
| meal_id | meal_name          | cuisine | cooking_time | vegetarian |
+---------+--------------------+---------+--------------+------------+
|       2 | Vegetable Stir Fry | Chinese |           20 |          1 |
|       4 | Mushroom Risotto   | Italian |           35 |          1 |
+---------+--------------------+---------+--------------+------------+
```

15) `select * from Meals order by cooking_time desc;`

```
+---------+---------------------+---------+--------------+------------+
| meal_id | meal_name           | cuisine | cooking_time | vegetarian |
+---------+---------------------+---------+--------------+------------+
|       3 | Chicken Curry       | Indian  |           50 |          0 |
|       1 | Spaghetti Bolognese | Italian |           45 |          0 |
|       4 | Mushroom Risotto    | Italian |           35 |          1 |
|       2 | Vegetable Stir Fry  | Chinese |           20 |          1 |
+---------+---------------------+---------+--------------+------------+
```

16) `select * from Meals order by cooking_time asc;`

```
+---------+---------------------+---------+--------------+------------+
| meal_id | meal_name           | cuisine | cooking_time | vegetarian |
+---------+---------------------+---------+--------------+------------+
|       2 | Vegetable Stir Fry  | Chinese |           20 |          1 |
|       4 | Mushroom Risotto    | Italian |           35 |          1 |
|       1 | Spaghetti Bolognese | Italian |           45 |          0 |
|       3 | Chicken Curry       | Indian  |           50 |          0 |
+---------+---------------------+---------+--------------+------------+
```

17) `select Meals.meal_name as Meals,

    ->     Ingredients.ingredient_name as Ingredients,
    
    ->     Ingredients.quantity as Quantity
    
    ->     from Meals
    
    ->     join Ingredients on Meals.meal_id = Ingredients.meal_id;`

```
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
```

18) `select ingredient_name as Ingredients,

    ->     quantity as Quantity
    
    ->     from Ingredients 
    
    ->     where meal_id = (select meal_id from Meals where meal_name = 'Chicken Curry');`

```    
+----------------+----------+
| Ingredients    | Quantity |
+----------------+----------+
| Chicken Breast | 300g     |
| Curry Powder   | 2T       |
| Coconut Milk   | 1cup     |
+----------------+----------+
```

19) `select cuisine, Count(*) as meal_count

    -> from Meals
    
    -> group by cuisine;`
    
```
+---------+------------+
| cuisine | meal_count |
+---------+------------+
| Italian |          2 |
| Chinese |          1 |
| Indian  |          1 |
+---------+------------+
```

20) `select meal_name, cooking_time 

    ->     from Meals 
    
    ->     where cooking_time <= 45
    
    ->     order by cooking_time asc;`
    
```
+---------------------+--------------+
| meal_name           | cooking_time |
+---------------------+--------------+
| Vegetable Stir Fry  |           20 |
| Mushroom Risotto    |           35 |
| Spaghetti Bolognese |           45 |
+---------------------+--------------+
```

21) `\q`

22) `sudo mysql -u root`

23) `show grants for 'opacuser'@'localhost';`

```
+----------------------------------------------------------------+
| Grants for opacuser@localhost                                  |
+----------------------------------------------------------------+
| GRANT USAGE ON *.* TO `opacuser`@`localhost`                   |
| GRANT ALL PRIVILEGES ON `DinnerDB`.* TO `opacuser`@`localhost` |
| GRANT ALL PRIVILEGES ON `opacdb`.* TO `opacuser`@`localhost`   |
+----------------------------------------------------------------+
```

24) `\q`

### Issues Encountered 

- Problem: Missing things like commas when typing.
  
- Solution: Be careful when typing and don't get furstrated when I get an error message.

### What I Learned

  I learned about relational tables. Meaning one table relies on infromation from another table. 
This way not all of the information needs to be conatined in one table. Also you won't have duplicate information. 
For example with our ingredients table doen't say whether the dish is vegetarian or not but we can still get that 
information becasue it is in the meals table. 

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

```
+------------------+
| Tables_in_opacdb |
+------------------+
| books            |
+------------------+
```

14) `select * from books;`

```
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
```

15) `insert into books

    -> (author, title, publisher, copyright) values
    
    -> ('Emma Donoghue', 'Room', 'Little, Brown & Company', '2010-01-01'),
    
    -> ('Zadie Smith', 'White Teeth', 'Hamish Hamilton', '2000-01-01');`
    
16) `select * from books;`

```
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
```

17) `delete from books where author='zadie smith';` : accidentally entered the information twice
so I wanted to delete the duplicates.

18) `delete from books where author='emma donoghue';`

19) `insert into books

     -> (author, title, publisher, copyright) values
     
     -> ('Emma Donoghue', 'Room', 'Little, Brown & Company', '2010-01-01'),
     
     -> ('Zadie Smith', 'White Teeth', 'Hamish Hamilton', '2000-01-01');`

20) `select * from books;`

```
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
```

### Issues Encountered 

- Problem: Be careful when using the up arrow in MySQL. That's how I ended up with duplicate records.
  
- Solution: Try to use the up arrow key as little as posible when in MySQL. It doesn't do what I want it to
  which is to move up in my code. 

### What I Learned

  I learned how to create a very simple OPAC. Now my book table is searchable via a website. 

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

### Issues Encountered 

- Problem: This section went fairly smooth for me. 
  
- Solution:

### What I Learned

  I learned how to make a simple cataloging module. Using this module I was able to add books to my
  books table (catalog) instead of having to code them in. This is a possible way a cataloger might 
  put in new books to the system. 
