there are 3 formats in MYSQL you need to set that according to your needs

`STATEMENT`
This will log every SQL statement that will insert or update a row to the bin log this is the one to go if you are replicating data to another db 

`ROW`
Every change to a row in represented as a line in the bin log not as SQL but the data in the row it self for a warehousing purposed this is the preferred way as warehousing the data doesn't care about the entity type too much

`MIXED`
This will log both the statement and row data this is not highly recommended as the disk space will double

to check the format use this SQL query

```
SELECT variable_value as bin_log_format
FROM performance_schema.global_variables
WHERE variable_name='binlog_format';
```

see also
- [[Debezium]]
- [[Check if bin_log is enabled]]