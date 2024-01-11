```
SELECT variable_value as bin_log_status
FROM performance_schema.global_variables
WHERE variable_name='log_bin';
```

see also
[[Debezium]]
[[SQL for checking replica identity for tables]]