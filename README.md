# SQL-75-CHALLENGE
75 SQL questions to enhance querying skills


**Question 1:**
A table named “famous” has two columns called user id and follower id. 
It represents each user ID has a particular follower ID. These follower IDs are also users of hashtag#Facebook / hashtag#Meta. Then, find the famous percentage of each user. 
Famous Percentage = number of followers a user has / total number of users on the platform.
𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE famous (user_id INT, follower_id INT);

INSERT INTO famous VALUES
(1, 2), (1, 3), (2, 4), (5, 1), (5, 3), 
(11, 7), (12, 8), (13, 5), (13, 10), 
(14, 12), (14, 3), (15, 14), (15, 13);
```sql
WITH distinct_users AS
(
SELECT  user_id as uid FROM Famous  UNION SELECT follower_id as uid FROM Famous
),
Follower_count AS
(
SELECT user_id, count(follower_id) as followers
FROM Famous
GROUP BY user_id
)
SELECT f.user_id, f.followers /(SELECT count(*) FROM distinct_users ) AS famous percentage
FROM Follower_count AS f;
```
