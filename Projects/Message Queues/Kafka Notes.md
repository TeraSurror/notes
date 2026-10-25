Concepts: 
**1. Topic:** A named category or feed that messages are published to. Producers write to a topic, and consumers read from it. For example, an `orders` topic might hold every order placed on a site.
**2. Partition:** A topic is split into one or more partitions, each an ordered, append-only log. Partitions let a topic scale: different partitions can live on different brokers and be read in parallel. Ordering is guaranteed only within a single partition, not across the whole topic.
**3. Offset:** A sequential ID that identifies each message’s position within a partition. The first message is offset 0, the next is 1, and so on. Consumers track their offset to know what they’ve already read, and they can rewind to an earlier offset to reprocess messages.
**4. Key:** An optional value attached to a message. The producer hashes the key to pick a partition, so all messages with the same key land in the same partition and stay in order. For example, using `user_id` as the key keeps each user’s events in sequence. Messages without a key are usually spread across partitions.
**5. Producer:** An application that writes (publishes) messages to a topic. It decides which partition each message goes to, either by key or by a partitioning strategy, and can choose how many acknowledgments to wait for before considering a write successful.
**6. Consumer:** An application that reads messages from a topic. Consumers usually belong to a consumer group, where each partition is assigned to one consumer in the group. That lets a group process a topic in parallel while each message is handled once per group. The consumer commits its offsets to record progress.
**7. Broker:** A server in the cluster that stores partitions and serves reads and writes from producers and consumers. A cluster has several brokers, and each partition is replicated across them so data survives a broker failure. One replica acts as the leader for reads and writes, and the others act as followers.
Putting it together: a producer sends a keyed message to a topic. The key determines the partition, the broker that leads that partition stores the message at the next offset, and a consumer in a group reads it by offset.

Facts in Kafka:
1. Ordering is per partition
2. Key decides the partition
3. Offsets are per partition

Consequence: If we have to process OrderPlaced -> OrderPaid -> OrderShipped in that sequence for a particular order, then we have to make sure that they all have the same key (eg order_id). This is because ordering happens per partition.

It is the consumers job to keep track of where the message are, so they can get all the information. The consumer should save it's offset

