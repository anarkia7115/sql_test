# sql_test
## PROBLEM 1
```sql
SELECT transaction_count, COUNT(1) AS customer_count
FROM ( 
    SELECT customer_id, COUNT(distinct transaction_id) AS transaction_count
    FROM payments_transactions
    GROUP BY customer_id ) AS trans_count_by_customer
GROUP BY transaction_count;
```
