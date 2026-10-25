
| Model      | Who gets each message                                             | What happens after it's read               | Examples               |
| ---------- | ----------------------------------------------------------------- | ------------------------------------------ | ---------------------- |
| Work queue | one of N competing workers                                        | deleted once acknowleged                   | RabbitMQ, SQS          |
| Pub/sub    | every current subscriber                                          | gone once delivered                        | SNS, Redis pub/sub     |
| Log        | anyone who reads it; each reader tracks its own position (offset) | kept for a set retention time, read or not | Kafka, Kinesis, Pulsar |
|            |                                                                   |                                            |                        |

Kafka is a log. The broker doesn't delete messages when they are read and doesn't track who has read what. Each consumer remembers its own offset and can rewind.

