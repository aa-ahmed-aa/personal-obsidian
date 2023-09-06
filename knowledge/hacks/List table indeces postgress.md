
```
SELECT tablename, indexname, indexdef 
FROM pg_indexes 
WHERE schemaname = 'public' 
and tablename = '<table name>'
ORDER BY tablename, indexname;
```