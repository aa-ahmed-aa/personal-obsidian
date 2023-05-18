Retention policy types
- `compaction` : removed the value if some producers use the same key
- `time based` : set the retention based on specific time frame so the data los will happen if the data expired

## Some Terms and Concep Ideas

#### ISR (in sync replica)
This identifies the consistent brokers this ISR array will have the list of brokers synced correctlly, later controleplane node elects any of the ISR brokers to be the leader if the leader is down

#### High watermark
is an index into the log file that records the last log entry that is known to have successfully replicated to a Quorum of followers. The leader also passes on the high-water mark to its followers during its replication.

#### leader epoch
a leader epoch refers to the number of leaders previously assigned by the controller. Every time a leader fails, the controller selects the new leader, increments the current "leader epoch" by 1, and shares the leader epoch with all replicas
