# SQL Homework

The local cinema are having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

## To access the database:

First, create a database called 'marvel'

```
# terminal
createdb marvel
```

Next, run the provided SQL script to populate your database:

```
# terminal
psql -d marvel -f marvel.sql
```

Use the supplied data as the source of data to answer the questions. Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.

## Questions

1.  Return ALL the data in the 'movies' table.
marvel=# SELECT * FROM movies;
id |                title                | year | show_time
----+-------------------------------------+------+-----------
 1 | Iron Man                            | 2008 | 15:10
 2 | The Incredible Hulk                 | 2008 | 13:05
 3 | Iron Man 2                          | 2010 | 23:55
 4 | Thor                                | 2011 | 20:30
 5 | Captain America: The First Avenger  | 2011 | 21:15
 6 | Avengers Assemble                   | 2012 | 21:15
 7 | Iron Man 3                          | 2013 | 23:30
 8 | Thor: The Dark World                | 2013 | 14:25
 9 | Batman Begins                       | 2005 | 18:05
10 | Captain America: The Winter Soldier | 2014 | 15:05
11 | Guardians of the Galaxy             | 2014 | 15:20
12 | Avengers: Age of Ultron             | 2015 | 21:15
13 | Ant-Man                             | 2015 | 19:45
14 | Captain America: Civil War          | 2016 | 14:30
15 | Doctor Strange                      | 2016 | 15:10
16 | Guardians of the Galaxy 2           | 2017 | 17:35
17 | Spider-Man: Homecoming              | 2017 | 17:20
18 | Thor: Ragnarok                      | 2017 | 20:10
19 | Black Panther                       | 2018 | 14:20
20 | Avengers: Infinity War              | 2018 | 14:50
21 | Ant-Man and the Wasp                | 2018 | 20:15
(21 rows)

2.  Return ONLY the name column from the 'people' table
marvel=# SELECT name FROM people;
            name             
-----------------------------
 Atyha   Arshad
 Calum Cannon
 Stelios Constantinou-Briggs
 Sridevi Dara
 Paul Flannery
 Lindsey Izzard
 Hugh Jarvis
 Tony Goncalves
 Scott Maitland
 David McAllister
 Mhairi McCrindle
 Anne McKendry
 John Muir
 Kevin OHagan
 Darren Shankland
 Danny   Welsh
 Theo Wright
 (17 rows)

3.  Oops! Someone at CodeClan spelled John's name wrong! Change it to reflect the proper spelling ('John Muir' should be 'John Moir').
UPDATE people SET name = 'John Moir' WHERE name = 'John Muir';

4.  Return ONLY your name from the 'people' table.
marvel=# SELECT name FROM people WHERE id = 2;
     name     
--------------
 Calum Cannon
(1 row)

5.  The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.
marvel=# DELETE FROM movies WHERE id = 9;
DELETE 1

6.  Create a new entry in the 'people' table with the name of one of the instructors.
marvel=# INSERT INTO people(name) VALUES ('Alistair Kane');
INSERT 0 1

7.  Tony Goncalves has decided to hijack our movie evening, Remove him from the table of people.
marvel=# DELETE FROM people WHERE name = 'Tony Goncalves';
DELETE 1

8.  The cinema has just heard that they will be holding an exclusive midnight showing of 'Captain Marvel'!! Create a new entry in the 'movies' table to reflect this.
marvel=# INSERT INTO movies(title,year,show_time) VALUES ('Captain Marvel', 2019, '00:00');
INSERT 0 1

9.  The cinema would also like to make the Guardians movies a back to back feature. Find out the show time of "Guardians of the Galaxy" and set the show time of "Guardians of the Galaxy 2" to start two hours later.
marvel=# UPDATE movies SET show_time = '17:20' WHERE id = 11;
UPDATE 1

## Extension

1.  Research how to delete multiple entries from your table in a single command.
marvel=# DELETE FROM movies WHERE id IN (1,2,3);
DELETE 3
