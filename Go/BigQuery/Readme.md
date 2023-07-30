1. Navigate to GCP console page.
   ![image](https://github.com/vibhordubey333/GCP-Tutorial/assets/22407855/45a895e7-2267-4a5f-9a45-4f0d15d8150c)
2. Select Public Datasets.
   ![image](https://github.com/vibhordubey333/GCP-Tutorial/assets/22407855/f9e8d757-0927-4476-babb-986d48ea0fec)
3. Click on Add then search for "Stack overflow" in public data sets.
   ![image](https://github.com/vibhordubey333/GCP-Tutorial/assets/22407855/6ad397df-d4a7-462c-b292-866b79149cd0)
4. Click on "Stack Overflow"
   ![image](https://github.com/vibhordubey333/GCP-Tutorial/assets/22407855/b2d4f6b9-f054-4ab3-aaf4-1e3969c7b471)
5. We've to perform query on badge table.
  
  ```
  SELECT badge_name AS First_Gold_Badge,
COUNT(1) AS Num_Users,
ROUND(AVG(tenure_in_days)) AS Avg_Num_Days
FROM
(
SELECT
badges.user_id AS user_id,
badges.name AS badge_name,
TIMESTAMP_DIFF(badges.date, users.creation_date, DAY) AS tenure_in_days,
ROW_NUMBER() OVER (PARTITION BY badges.user_id
ORDER BY badges.date) AS row_number
FROM
`bigquery-public-data.stackoverflow.badges` badges
JOIN
`bigquery-public-data.stackoverflow.users` users
ON badges.user_id = users.id
WHERE badges.class = 1
)
WHERE row_number = 1
GROUP BY First_Gold_Badge
ORDER BY Num_Users DESC
LIMIT 10
  ```

   ![image](https://github.com/vibhordubey333/GCP-Tutorial/assets/22407855/8b5aca9c-1ebb-468f-b570-c9f615156e1f)
