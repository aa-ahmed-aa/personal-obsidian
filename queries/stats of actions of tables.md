```
SELECT schemaname, relname as table_name, n_tup_ins AS insert_count, n_tup_upd AS update_count, n_tup_del AS delete_count
FROM pg_stat_all_tables
WHERE schemaname = 'public';
```