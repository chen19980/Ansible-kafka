# (kafka 3.0 之後不再依賴zookeeper 改使用 kRaft)
# 啟動kafka
sh kafka-server-start.sh /path/to/config/kraft/server.properties

# 停止kafka
bash kafka-server-stop.sh /path/to/config/kraft/server.properties

# 產生 cluster-id (叢集 UUID)
sh kafka-storage.sh random-uuid

# 格式化儲存 (設定日誌儲存格式)
sh kafka-storage.sh format -t <cluster-id> -c /path/to/config/kraft/server.properties

# 建立 topic
sh kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor<複本數量> 1 --partitions 1 --topic <topic_name>

# 查看 topic
sh kafka-topics.sh --list --bootstrap-server localhost:9092

# 刪除 topic
sh kafka-topics.sh --delete --topic <topic_name> --bootstrap-server loca
lhost:9092

# 發布 event to topic
sh kafka-console-producer.sh --topic <topic_name> --bootstrap-server localhost:9092

# 接收 event from topic
sh kafka-console-consumer.sh --topic <topic_name> --bootstrap-server localhost:9092

# 顯示topic的詳細資料
sh kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic <topic_name>

# 建立新的consumer
sh kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic <topic_name> --new-consumer --from-beginning --consumer.config config/consumer.properties

# 新增Topic partition
sh kafka-add-partitions.sh --topic <topic_name> --partition 2 --bootstrap-server localhost:9092
