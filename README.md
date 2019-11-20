# sql_test
## PROBLEM 1
```sql
-- suppose payments transactions table is called **payments_transactions**

CREATE TABLE payment_number_distribution AS
SELECT transaction_count, COUNT(1) AS customer_count
FROM ( 
    SELECT customer_id, COUNT(distinct transaction_id) AS transaction_count
    FROM payments_transactions
    GROUP BY customer_id ) AS trans_count_by_customer
GROUP BY transaction_count;

SELECT *
FROM payment_number_distribution;
```

## PROBLEM 2
```sql
-- use table created in PROBLEM 1
SELECT at_least_n_transaction.tansaction_count, sum(details.customer_count) as customer_count
FROM payment_number_distribution AS details
    JOIN payment_number_distribution AS at_least_n_transaction
    ON details.transaction_count >= at_least_n_transaction.tansaction_count
```

## PROBLEM 3
```sql
-- suppose friends table called **friends**
SELECT friend1_s_friends.friend1, friend2_s_friends.friend2, COUNT(distinct friend1_s_friends.friend2) AS mutual_friends_count
FROM friends AS friend1_s_friends
JOIN friends AS friend2_s_friends
ON friend1_s_friends.friend2 = friend2_s_friends.friend1
```
