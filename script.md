CORRESPONDING DATABASE IS LOCATED IN
../Desktop/Homework/Databases/Fringeshows - ENSURE THE QUERIES ARE ONLY PERFORMED IN THIS DIRECTORY**

Revision of concepts that we've learnt in SQL today

Select the names of all users.
SELECT * from USERS;
 id |       name       
----+------------------
  1 | Rick Henri
  2 | Jay Chetty
  3 | Keith Douglas
  4 | Callum Dougan
  5 | Andrew Insley
  6 | Daniel Gillespie
  7 | Bethany Fraser
  8 | Nick Ridell
  9 | Evelyn Utterson
 10 | Sky Su
 11 | Nicholas Hill
 12 | Michael McLeod
 13 | Callum Hogg
 14 | Chris Sloan
 15 | Gary Carmichael
 16 | Oscar Brooks
 17 | Ross Galloway
 18 | Paul MacLean
 19 | Stuart Ramsay
 20 | Peter Forbes
 21 | Euan Walls
 22 | Aine Dunphy
(22 rows)

Select the names of all shows that cost less than £15.
SELECT name from SHOWS WHERE price < 15.00;
             name             
------------------------------
 Le Haggis
 Paul Dabek Mischief 
 Best of Burlesque
 Two become One
 Urinetown
 Two girls, one cup of comedy
(6 rows)

Insert a user with the name "Val Gibson" into the users table.
INSERT INTO users (name) VALUES ('Val Gibson');
INSERT 0 1

Select the id of the user with your name.
SELECT id from users where name = 'Stuart Ramsay';
 id 
----
 19
(1 row)

Insert a record that Val Gibson wants to attend the show "Two girls, one cup of comedy".
INSERT INTO shows_users (show_id, user_id) VALUES (12,23);
INSERT 0 1


Updates the name of the "Val Gibson" user to be "Valerie Gibson".
UPDATE users SET name = 'Valerie Gibson' WHERE name = 'Val Gibson';
UPDATE 1


Deletes the user with the name 'Valerie Gibson'.
DELETE from users WHERE name = 'Valerie Gibson';
DELETE 1



Deletes the shows for the user you just deleted.
DELETE from shows_users WHERE user_id = 23;
DELETE 1


Section 2

This section involves more complex queries. You will need to go and find out about aggregate funcions in SQL to answer some of the next questions.

Select the names and prices of all shows, ordered by price in ascending order.
SELECT name, price from shows ORDER BY price ASC;
                   name                    | price 
-------------------------------------------+-------
 Two girls, one cup of comedy              |  6.00
 Best of Burlesque                         |  7.99
 Two become One                            |  8.50
 Urinetown                                 |  8.50
 Paul Dabek Mischief                       | 12.99
 Le Haggis                                 | 12.99
 Joe Stilgoe: Songs on Film â€“ The Sequel | 16.50
 Game of Thrones - The Musical             | 16.50
 Shitfaced Shakespeare                     | 16.50
 Aaabeduation â€“ A Magic Show             | 17.99
 Camille O'Sullivan                        | 17.99
 Balletronics                              | 32.00
 Edinburgh Royal Tattoo                    | 32.99
(13 rows)



Select the average price of all shows.
SELECT AVG(price) from shows;
         avg         
---------------------
 15.9569230769230769
(1 row)





Select the price of the least expensive show.
SELECT MIN(price) from shows;
 min  
------
 6.00
(1 row)


Select the sum of the price of all shows.
SELECT SUM(price) from shows;
  sum   
--------
 207.44
(1 row)


Select the sum of the price of all shows whose prices is less than £20.
SELECT SUM(price) from shows WHERE price <20.00;
  sum   
--------
 142.45
(1 row)

Select the name and price of the most expensive show.
SELECT name,price from shows WHERE price=(select max(price) from shows);
          name          | price 
------------------------+-------
 Edinburgh Royal Tattoo | 32.99
(1 row)





Select the name and price of the second from cheapest show.




Select the names of all users whose names start with the letter "N".
SELECT name from users where name LIKE 'N%';
     name      
---------------
 Nick Ridell
 Nicholas Hill
(2 rows)



Select the names of users whose names contain "mi".
select name from users where name like '%mi%';
      name       
-----------------
 Gary Carmichael
(1 row)

***Why does it not bring up Michael??**


Section 3

The following questions can be answered by using nested SQL statements but ideally you should learn about JOIN clauses to answer them.

Select the time for the Edinburgh Royal Tattoo.

**INCORRECT - CLOSEST ANSWER I GOT!
SELECT time from times INNER JOIN shows on shows.name = shows.name;



Select the number of users who want to see "Shitfaced Shakespeare".

Select all of the user names and the count of shows they're going to see.

SELECT all users who are going to a show at 17:15.