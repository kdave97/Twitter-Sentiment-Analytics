# Twitter-Sentiment-Analytics

## Project Description
The project focuses on processing live data streams using Spark's streaming API. We perform sentiment analysis of the realtime tweets. We also use Apache Kafka to buffer the tweets before processing.

## Dataset Description
We will be using the twitter data which can be downloaded from the below link:
https://drive.google.com/open?id=1AXiumYL4lYSitWp3TMQMvGKLMWZnsFPP

## Steps Performed
* Download the data from the above link and unzip it.
* Start the zookeeper service - $KAFKA_HOME/bin/zookeeper-server-start.sh $KAFKA_HOME/config/zookeeper.properties
* Start Kafka service - $KAFKA_HOME/bin/kafka-server-start.sh $KAFKA_HOME/config/server.properties
* Create a topic named twitterstream in kafka - $KAFKA_HOME/bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1   --partitions 1 --topic twitterstream
* Run python twitter_to_kafka.py to stream the tweets and push them to kafka queue
* Run the stream analysis program - $SPARK_HOME/bin/spark-submit --packages org.apache.spark:spark-streaming-kafka-0-8_2.11:2.0.0
twitterStream.py