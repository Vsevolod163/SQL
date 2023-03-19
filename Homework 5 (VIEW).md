USE vk;

---

CREATE OR REPLACE VIEW users_view_info AS
	SELECT users.id, users.firstname, users.lastname, users.phone, profiles.gender, profiles.birthday
	FROM users
	JOIN profiles on users.id = profiles.user_id;

---

SELECT * 
FROM users_view_info
WHERE gender = "f"
GROUP BY id
ORDER BY firstname 
LIMIT 7;

---

DROP VIEW users_view_info;