# Kafka Foundatons
### Installing Apache kafka
```
wget http://apache.mirrors.spacedump.net/kafka/2.4.0/kafka_2.12-2.4.0.tgz
tar -xzf kafka_2.12-2.4.0.tgz
cd kafka_2.12-2.4.0
```

### Start Kafka ZooKeeper
```
sudo bin/zookeeper-server-start.sh config/zookeeper.properties
```

### Start Kafka Server
```
sudo bin/kafka-server-start.sh config/server.properties}}
```

### **Topics can be descibed with kafka-topics tool**
```
bin/kafka-topics.sh --bootstrap-server localhost:9092 --describe
```

### List topics short
```
bin/kafka-topics.sh --list --zookeeper localhost:2181
```

### Start Wordcount Application
```
bin/kafka-run-class.sh org.apache.kafka.streams.examples.wordcount.WordCountDemo
```

### Start console producer on a separate terminal
```
bin/kafka-console-producer.sh --broker-list localhost:9092 --topic streams-plaintext-input
```
--- 
# Bachelorproject start
### Start confulent dev-server
```
sudo docker-compose up
```

### Start confluent tools
```
sudo docker run -it --rm --net=host confluentinc/cp-schema-registry:3.3.1 bash
```

# Anderes
### Create Topic
```
./bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic saledorder
```

### Kafka delte topic
In kafka root folder:
```
bin/kafka-topics.sh --zookeeper localhost:2181 --delete --topic DummyTopic
```

### Delete Records
```
./bin/kafka-delete-records.sh --bootstrap-server localhost:9092 --offset-json-file ./offsetfile.json
```

### Start Confluence tools
```
sudo docker run --net=host -it confluentinc/cp-schema-registry:3.3.0 bash
```

### Produce record with one field
```
# Produce a record with one field
kafka-avro-console-producer \
    --broker-list 127.0.0.1:9092 --topic test-avro \
    --property schema.registry.url=http://127.0.0.1:8081 \
    --property value.schema='{"type":"record","name":"myrecord","fields":[{"name":"f1","type":"string"}]}'
```

```
{"f1": "value1"}
```

## Producer test
```
# Produce a record with one field
kafka-avro-console-producer \
    --broker-list 127.0.0.1:9092 --topic order_created-in \
    --property schema.registry.url=http://127.0.0.1:8081 \
    --property value.schema='{
  "type" : "record",
  "name": "test",
      "fields" : [ {
        "name" : "name",
        "type" : "string"
      }, {
        "name" : "APropertie",
        "type" : {
          "type" : "array",
          "items" : {
            "type" : "record",
            "name" : "APropertie",
            "fields" : [ {
              "name" : "key",
              "type" : "string"
            }, {
              "name" : "name",
              "type" : "string"
            }, {
              "name" : "date",
              "type" : "string"
            } ]
          }
        }
      } ]
}'
```

```
{"name": "order_created", "APropertie": [{"key": "1", "name": "testname", "date": "testdate"}]}
```

```
# Produce a record with one field
kafka-avro-console-producer \
    --broker-list 127.0.0.1:9092 --topic order_created-in \
    --property schema.registry.url=http://127.0.0.1:8081 \
    --property value.schema='{"type":"record","name":"test","fields":[{"name":"name","type":"string"},{"name":"APropertie","type":{"type":"array","items":{"type":"record","name":"APropertie","fields":[{"name":"key","type":"string"},{"name":"name","type":"string"},{"name":"date","type":"string"}]}}}]}'

```