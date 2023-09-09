there are 3 formats in MYSQL you need to set that according to your needs

`STATEMENT`
This will log every SQL statement that will insert or update a row to the bin log this is the one to go if you are replicating data to another db 

`ROW`
Every change to a row in represented as a line in the bin log not as SQL but the data in the row it self for a warehousing purposed this is the preferred way as warehousing the data doesn't care about the entity type too much

`MIXED`
This will log both the statement and row data this is not highly recommended as the disk space will double

[[Debezium]]
[[Check if bin_log is enabled]]