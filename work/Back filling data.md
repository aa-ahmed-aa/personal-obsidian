if you add new consumer you will need to back fill this new table you created so go with these steps
-   export data from source table
`psql -h <DB_HOST> -d <DB_NAME> -U <DB_USER> -c "copy(SELECT factory_id, location_id, variant_id, in_stock, committed, expected, created_at, updated_at FROM inventory_levels) to stdout" > inventory_levels_staging.tsv`

-   import data to target table
`psql -h <DB_HOST> -d <DB_NAME> -U <DB_USER> -c "truncate table inventory_levels; copy inventory_levels(factory_id, location_id, variant_id, in_stock, committed, expected, created_at, updated_at) from stdin" < inventory_levels_staging.tsv`