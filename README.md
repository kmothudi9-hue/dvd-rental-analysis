# DVD Rental Analysis — Top 10 Most Rented Movies

## Overview
This project analyzes a DVD rental business to identify which movies drive the most rentals. Built as Project 1 of my Data Analyst portfolio.

## Tools Used
- PostgreSQL (SQL: JOINs, GROUP BY, ORDER BY, LIMIT)
- Python (Pandas for data exploration)
- GitHub

## Business Question
Which 10 movies are rented the most, and what does that tell us about customer demand?

## Process
1. Queried `dvdrental` database in PostgreSQL
2. Joined film -> inventory -> rental tables
3. Aggregated rentals per movie title
4. Exported results for Python visualization (next step)

## Key SQL Query
```sql
SELECT f.title, COUNT(r.rental_id) AS rental_count
FROM film f
JOIN inventory i ON f.film_id = i.film_id
JOIN rental r ON i.inventory_id = r.inventory_id
GROUP BY f.title
ORDER BY rental_count DESC
LIMIT 10;
