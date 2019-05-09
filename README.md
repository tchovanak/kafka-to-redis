# File data to Redis through Kafka
## Overview
POC Redis Sink Connector
## Run the Pipeline

### Start Services

```bash
docker-compose up
```

After services fully start, visit

- [Kafka topics UI](http://localhost:8000)
- [Kafka Connect UI](http://localhost:8003)

### Create Connectors

```bash
# file source connector for topic: analytics.server.logs
curl -X POST http://localhost:8083/connectors \
    -H 'Content-Type:application/json' \
    -H 'Accept:application/json' \
    -d @connectors/connect.source.file.analytics.server.logs.json

# file source connector for topic: analytics.user.events
curl -X POST http://localhost:8083/connectors \
    -H 'Content-Type:application/json' \
    -H 'Accept:application/json' \
    -d @connectors/connect.source.file.analytics.user.events.json

# redis sink connector for all topics
curl -X POST http://localhost:8083/connectors \
    -H 'Content-Type:application/json' \
    -H 'Accept:application/json' \
    -d @connectors/connect.sink.redis.json
```

## Generate Data

### Write data to files

```bash
# messages for topic: analytics.server.logs
echo '{"ts":1528697281001,"id":"ac1393","log":"Nam congue pretium ligula, ac susc ."}' >> data/analytics.server.logs.txt
echo '{"ts":1528697281002,"id":"ac1393","log":"Quisque pretium justo massa, ac laet"}' >> data/analytics.server.logs.txt

# messages for topic: analytics.user.events
echo '{"ts":1528591539001,"id":"12bfc4","event":"login"}'  >> data/analytics.user.events.txt
echo '{"ts":1528592539001,"id":"12bfc4","event":"logout"}' >> data/analytics.user.events.txt
echo '{"ts":1528593539001,"id":"12bfc4","event":"login"}'  >> data/analytics.user.events.txt
echo '{"ts":1528594539001,"id":"12bfc4","event":"logout"}' >> data/analytics.user.events.txt
```

### View Data in Redis

- Open [Redis Commander UI](http://localhost:8881)
- Sample data should have been populated in the UI

## References

- [Apache Kafka Documentation - Connect](https://kafka.apache.org/documentation/#connect)
- [Confluent Docker Configuration](https://docs.confluent.io/current/installation/docker/docs/configuration.html)
- [Confluent Kafka Connect REST API](https://docs.confluent.io/current/connect/references/restapi.html)
- [Confluent Redis Sink Connector](https://jcustenborder.github.io/kafka-connect-documentation/projects/kafka-connect-redis/sinks/RedisSinkConnector.html)
