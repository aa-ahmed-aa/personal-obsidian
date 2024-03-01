use this query to check the dead tuples

https://aws.amazon.com/blogs/database/hidden-dangers-of-duplicate-key-violations-in-postgresql-and-how-to-avoid-them

```
SELECT relname, n_dead_tup, n_live_tup 
FROM pg_stat_user_tables 
WHERE relname = 'sales_orders';
```
