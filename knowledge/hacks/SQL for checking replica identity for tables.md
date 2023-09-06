```
SELECT CASE C.relreplident
       WHEN 'd' THEN 'default'
       WHEN 'n' THEN 'nothing'
       WHEN 'f' THEN 'full'
       WHEN 'i' THEN 'index'
    END AS replica_identity,
 C.relname
FROM pg_class C
LEFT JOIN pg_namespace N ON (N.oid = C.relnamespace)
WHERE
    nspname NOT IN (
        'pg_catalog',
        'information_schema'
    )
AND C.relkind ='r'
AND nspname !~ '^pg_toast';
```