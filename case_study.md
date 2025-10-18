# Video Game Sales Analysis

## Dataset

You will be working with the following dataset: [Video Game Sales](https://www.kaggle.com/datasets/gregorut/videogamesales?resource=download)

📦 **Dataset Download Instructions**
1. Download the dataset ZIP file from the above link.
2. After downloading: Unzip the file to access vgsales.csv. Note the full file path to vgsales.csv — you'll need it in the next step.

🔍 **Challenge: Load the Data into DuckDB**
Using DBeaver and your DuckDB connection, how would you load the vgsales.csv file into a table so you can begin querying it?

## Business Question
How can game developers and publishers optimize their strategy to maximize global sales by understanding the performance of different game genres, platforms, and publishers?

*To answer the above question, use the following SQL queries to explore the dataset and address the following questions:*

Which genres contribute the most to global sales?

SQL:
```sql
SELECT
  genre,
  SUM(global_sales)         AS total_sales
FROM vgsales
GROUP BY genre
ORDER BY total_sales DESC;
```
Findings:
```findings
Action is the hightest
```
Which platforms generate the highest global sales?

SQL:
```sql
SELECT
  platform,
  SUM(global_sales) AS total_sales
FROM vgsales
GROUP BY platform
ORDER BY total_sales DESC;
```
Findings:
```findings
PS2 is the highest
```
Which publishers are the most successful in terms of global sales?

SQL:
```sql
SELECT
    publisher,
    SUM(global_sales) AS total_sales
FROM vgsales
GROUP BY publisher
ORDER BY total_sales DESC;
```
Findings:
```findings
Nintendo is most successful publishers
```
How does success vary across regions (North America, Europe, Japan, Others)?

SQL:
```sql
SELECT
    SUM(na_sales) AS total_north_america_sales,
    SUM(eu_sales) AS total_europe_sales,
    SUM(jp_sales) AS total_japan_sales,
    SUM(other_sales) AS total_other_sales
FROM
    vgsales;
```
Findings:
```findings
Total North America Sales is 4392.950000000332
Total Europe Sales is 2434.13000000055
Total Japan Sales is 1291.0199999999018
Total Other sales is 797.7499999998826
```
What are the trends over time in game sales by genre and platform?

SQL:
```sql
SELECT
    year,
    genre,
    SUM(global_sales) AS total_sales
FROM
    vgsales
WHERE
    year IS NOT NULL
GROUP BY
    year, genre
ORDER BY
    year ASC, total_sales DESC;
```
Findings:
```findings

```
Which platforms are most successful for specific genres?

SQL:
```sql
SELECT
    genre,
    platform,
    SUM(global_sales) AS total_sales
FROM
    vgsales
GROUP BY
    genre, platform
ORDER BY
    genre ASC, total_sales DESC;
```
Findings:
```findings
PS3 is most successful for Action Genre
```
## Deliverables:
- SQL Queries: Provide all the SQL queries you used to answer the business questions.
- Summary of Findings: For each question, summarise your key findings and recommendations based on your analysis.

## Submission

- Submit the GitHub URL of your assignment to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
