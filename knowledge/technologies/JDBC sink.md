The Kafka Connect JDBC Sink connector allows you to export data from Apache Kafka® topics to any relational database with a JDBC driver. This connector can support a wide variety of databases. The connector polls data from Kafka to write to the database based on the topics subscription. It is possible to achieve idempotent writes with upserts. Auto-creation of tables and limited auto-evolution is also supported.

docs link https://docs.confluent.io/kafka-connectors/jdbc/current/sink-connector/overview.html

look at [[Debezium]] to check differencies between this and debezium connector


see also
- [[Debezium]]