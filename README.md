# 🎬 Netflix Content Analytics (SQL Project)

## 📌 Project Overview
This project analyzes Netflix Movies and TV Shows using SQL to extract insights such as:
- Distribution of Movies vs TV Shows
- Top 10 countries with the most content
- Most common genres
- Longest movies
- Content trends over the years

Dataset Source: [Netflix Movies and TV Shows (Kaggle)](https://www.kaggle.com/datasets/shivamb/netflix-shows)

---

## 🛠 Tools & Technologies
- SQL (MySQL / PostgreSQL)
- Kaggle Dataset
- Data Modeling
- Window Functions, CTEs, Stored Procedures

## SQL Queries
```sql
-- Count Total Movies vs TV Shows
SELECT 
    type, COUNT(type) AS Total
FROM
    netflix
GROUP BY type
ORDER BY Total DESC;

-- Find the Top 10 Countries with the Most Content
SELECT 
    country, COUNT(*) AS Total
FROM
    netflix
WHERE
    country IS NOT NULL
GROUP BY country
ORDER BY Total DESC
LIMIT 10;

-- Most Common Genres on Netflix
SELECT 
    listed_in, COUNT(*) AS Total
FROM
    netflix
WHERE
    listed_in IS NOT NULL
GROUP BY listed_in
ORDER BY total DESC
LIMIT 5;

-- New Content Added Each Year
SELECT 
    YEAR(date_added) AS Add_Year, COUNT(*) AS Total
FROM
    netflix
WHERE
    date_added IS NOT NULL
GROUP BY Add_Year
ORDER BY Total DESC;

-- Movies/Shows by Rating
SELECT 
    rating, COUNT(*) AS Total
FROM
    netflix
WHERE
    rating IS NOT NULL
GROUP BY rating
ORDER BY Total DESC;

-- Most Frequent Directors

SELECT 
    director, COUNT(*) AS total_movies
FROM
    netflix
WHERE
    director IS NOT NULL
GROUP BY director
ORDER BY total_movies DESC
LIMIT 10;

-- Create a View for Top 20 Movies by Country
CREATE VIEW top_movies_per_country AS
    SELECT 
        country, title, release_year
    FROM
        netflix
    WHERE
        type = 'Movie' AND country IS NOT NULL
    ORDER BY country , release_year DESC
    LIMIT 20;



```
## 📊 Key Insights
- Movies form 70% of the catalog, while TV Shows are 30%.
- The US, India, and the UK dominate Netflix content.
- Dramas and Comedies are the most frequent genres.
- Netflix has rapidly increased content since 2017.

---

## 📂 Repository Structure
