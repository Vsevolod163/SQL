USE vk;

----

-- Подсчитать количество групп, в которые вступил каждый пользователь.

SELECT users.id, COUNT(users_communities.community_id) as number_of_communitites

FROM users

LEFT JOIN users_communities ON users.id = users_communities.user_id

GROUP BY users.id;

---

-- Подсчитать количество пользователей в каждом сообществе.

SELECT communities.id, COUNT(users_communities.user_id) as number_of_users

FROM communities

LEFT JOIN users_communities ON communities.id = users_communities.community_id

GROUP BY communities.id;

---

/*
Пусть задан некоторый пользователь. Из всех пользователей 
соц. сети найдите человека, который больше всех общался с выбранным 
пользователем (написал ему сообщений).
*/

SELECT users.id, COUNT(messages.id) AS message_count

FROM users

JOIN messages ON users.id = messages.from_user_id

WHERE messages.to_user_id = 2

GROUP BY users.id

ORDER BY message_count DESC

LIMIT 1;

---

-- *Подсчитать общее количество лайков, которые получили пользователи младше 18 лет

SELECT profiles.user_id, COUNT(likes.id)

FROM profiles

JOIN likes ON profiles.user_id = likes.user_id

WHERE TIMESTAMPDIFF(YEAR, birthday, CURDATE()) < 18

GROUP BY profiles.user_id;