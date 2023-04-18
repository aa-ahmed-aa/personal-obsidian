Is a CDC open source software to handel data delivery between multiple datasources

docs link : https://debezium.io/documentation/reference/stable/index.html

in this context here [[Debezium]] connector and [JDBC sink] 

[[Debezium]] will stream database/table changes to a kafka-topic
[[JDBC sink]] will stream the changes from your kafka topic to database table

you can use both together to replicate data between microservices and to keep consistency between other replica.


best practise is to name you topic like this `cdc-debezium.<db_name>.<table_name>`
