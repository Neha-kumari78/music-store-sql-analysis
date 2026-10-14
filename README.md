# Music Store Sales Analysis (SQL)

SQL analysis of a digital music store database to answer business questions about revenue, customer value, artist popularity and genre trends. The goal is to turn raw sales data into insights that can support marketing and business decisions.

## Tools Used
- PostgreSQL
- pgAdmin (or any SQL client)

## Database Overview
The database has these tables: `employee`, `customer`, `invoice`, `invoice_line`, `track`, `album`, `artist`, `genre`.

## SQL Concepts Used
- `JOIN` across multiple tables (up to 6)
- Aggregations: `SUM`, `COUNT`, `AVG`, `GROUP BY`
- Subqueries
- Common Table Expressions (CTEs)
- Window functions: `ROW_NUMBER()` with `PARTITION BY`

## Questions Answered

| # | Business Question | Concepts |
|---|-------------------|----------|
| 1 | Who is the most senior employee? | `ORDER BY`, `LIMIT` |
| 2 | Which countries have the most invoices? | `GROUP BY`, `COUNT` |
| 3 | What are the top 3 invoice totals? | `ORDER BY`, `LIMIT` |
| 4 | Which city generated the most revenue (for a promotional music festival)? | `SUM`, `GROUP BY` |
| 5 | Who is the best customer (highest spend)? | `JOIN`, `SUM` |
| 6 | Who are the Rock music listeners (email, name, genre)? | Multi-table `JOIN`, `DISTINCT` |
| 7 | Which 10 artists have the most Rock tracks? | `JOIN`, `COUNT` |
| 8 | Which tracks are longer than the average track length? | Subquery, `AVG` |
| 9 | How much did each customer spend on the best-selling artist? | CTE, `JOIN`, `SUM` |
| 10 | What is the most popular genre in each country? | CTE, `ROW_NUMBER()` |
| 11 | Who is the top-spending customer in each country? | CTE, `ROW_NUMBER()` |

## Key Insights

- **Best city for a promotional festival:** `<city name>` with total sales of `<amount>` (Q4)
- **Best customer overall:** `<customer name>` with total spending of `<amount>` (Q5)
- **Country with the most invoices:** `<country>` with `<count>` invoices (Q2)
- **Top Rock artist by track count:** `<artist name>` with `<count>` tracks (Q7)
- **Best-selling artist:** `<artist name>` with total sales of `<amount>`, and top spender on this artist is `<customer name>` (Q9)
- **Most popular genre:** `<genre>` is the top genre in most countries (Q10)

## Notes on the Approach
- For Q9, spend is calculated from `invoice_line` (unit price x quantity), because the invoice total can include several products and cannot be attributed to a single artist.
- For Q10 and Q11, `ROW_NUMBER()` with `PARTITION BY country` is used to pick the top genre and top customer within each country.
- For Q6, a subquery on `track` and `genre` is used to find all customers who bought Rock tracks.




