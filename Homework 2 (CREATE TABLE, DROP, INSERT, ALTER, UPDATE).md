  -------------------------

USE vk;

---------------------------

DROP TABLE IF EXISTS hobbies;

-------------------------
 
CREATE TABLE hobbies(

	hobby_id BIGINT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY, 
	
	hobby_name VARCHAR(100) NOT NULL,
	
    hobby_type VARCHAR(100) NOT NULL,
    
    INDEX name_hobby_index(hobby_name),\
    
	FOREIGN KEY (hobby_id) REFERENCES users(id)
	
 );
 
 -------------------------

 DROP TABLE IF EXISTS presents;
 
-------------------------
 
 CREATE TABLE presents(
 
	present_id BIGINT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY, 
	
    present_name VARCHAR(100) NOT NULL,
    
    present_letter TEXT NOT NULL,
    
    INDEX name_letter_index(present_name),
    
    FOREIGN KEY(present_id) REFERENCES users(id)
    
 );
 
 -------------------------
  
 INSERT INTO users(id, firstname, lastname, email, password_hash, phone)
  
 VALUES 
 
 (1, 'John', 'Craw', 'john@gmail.com', 'afagag', '35235235'),
 
 (2, 'Mike', 'Rote', 'mike@gmail.com', 'ewewbsd', '346346'),
 
 (3, 'Robert', 'Prote', 'robert@gmail.com', 'bdfgdsga', '4567332'),
 
 (4, 'Michael', 'Home', 'michael@gmail.com', 'dfsvaa', '723512'),
 
 (5, 'Peter', 'Klone', 'peter@gmail.com', 'fdhsawq', '5752342'),
 
 (6, 'Dilan', 'Monro', 'dilan@gmail.com', 'nkfksdwdg', '949694682'),
 
 (7, 'Alexey', 'Morev', 'alexey@gmail.com', 'dfwetqrq', '343737'),
 
 (8, 'Bob', 'Master', 'bob@gmail.com', 'lldglsh', '856873452'),
 
 (9, 'Cristian', 'Lenov', 'cristian@gmail.com', 'agmwlqwq', '939135113'),
 
 (10, 'Kostantin', 'Pirogov', 'konstantin@gmail.com', 'dlowplpdfw', '75325321');
 
  -------------------------
 
 INSERT INTO hobbies(hobby_id, hobby_name, hobby_type)
 
 VALUES 
 
 (1, 'volleyball', 'sport'),
 
 (2, 'guitar', 'music'),
 
 (3, 'computer games', 'computer'),
 
 (4, 'read books', 'books'),
 
 (5, 'songs', 'music'),
 
 (6, 'basketball', 'sport'),
 
 (7, 'drums', 'music'),
 
 (8, 'making photos', 'art'),
 
 (9, 'paint pictures', 'art'),
 
 (10, 'singing', 'music');

  -------------------------
 
 INSERT INTO profiles(user_id, gender, birthday)
 
 VALUES 
 
 (1, 'm', '1997-07-15'),
 
 (2, 'm', '2005-01-07'),
 
 (3, 'm', '2010-03-09'),
 
 (4, 'm', '2011-05-11'),
 
 (5, 'm', '2017-04-19'),
 
 (6, 'm', '2008-02-09'),
 
 (7, 'm', '2014-08-21'),
 
 (8, 'm', '2011-07-27'),
 
 (9, 'm', '2001-04-10'),
 
 (10, 'm', '1997-11-18');

 -------------------------

 INSERT INTO messages(id, from_user_id, to_user_id, created_at)
 
 VALUES 
 
 (1, 1, 2, '2024-07-15'),
 
 (2, 3, 4, '2005-01-07'),
 
 (3, 2, 5, '2025-03-09'),
 
 (4, 1, 9, '2011-05-11'),
 
 (5, 3, 7, '2029-04-19'),
 
 (6, 5, 1, '2008-02-09'),
 
 (7, 9, 10, '2021-08-21'),
 
 (8, 4, 2, '2011-07-27'),
 
 (9, 8, 1, '2030-04-10'),
 
 (10, 10, 3, '1997-11-18');

  -------------------------

ALTER TABLE profiles 

ADD COLUMN is_active BOOLEAN DEFAULT FALSE;

  -------------------------

UPDATE profiles 

SET is_active = TRUE 

WHERE TIMESTAMPDIFF(YEAR, birthday, CURDATE()) < 18;

 -------------------------

DELETE FROM messages 

WHERE created_at > CURDATE();