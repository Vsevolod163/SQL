 ------------
 
USE VK;

-----------------------------------------------------

SELECT DISTINCT firstname 
FROM users
ORDER BY firstname;

------------

SELECT COUNT( * ) AS count
FROM profiles
WHERE gender = "m" AND TIMESTAMPDIFF(YEAR, birthday, CURDATE()) > 35;

---------------------------

SELECT status, COUNT( * ) AS count
FROM friend_requests
GROUP BY status;

---------------------------

SELECT initiator_user_id, COUNT(*) AS num_requests
FROM friend_requests
GROUP BY initiator_user_id
ORDER BY num_requests DESC
LIMIT 1;