### why you should do that ?
This is necessary for Debezium to include `before` value of the entity in the kafka message

### How to set it ?
replication identity identifies if all columns should apear in the [[Debezium]] event 
so apply it use this query 
`ALTER TABLE <TABLE_NAME> REPLICA IDENTITY FULL;`

to check if it is set to full or not use
`SELECT relreplident FROM pg_class WHERE relname = '<TABLE_NAME>';
`
If the result is 'd', it means that the REPLICA IDENTITY for the table is set to 'FULL', which means that all columns are included in the replication data.

If the result is 'n', it means that the table is not a regular table or is not visible to the current user, and therefore does not have a REPLICA IDENTITY setting.