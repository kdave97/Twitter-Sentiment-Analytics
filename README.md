# Twitter-Sentiment-Analytics

## Project Description
The project focuses on processing live data streams using Spark's streaming API. We perform sentiment analysis of the realtime tweets. We also use Apache Kafka to buffer the tweets before processing.

## Dataset Description
We will be using the twitter data which can be downloaded from the below link: <br>
https://drive.google.com/open?id=1AXiumYL4lYSitWp3TMQMvGKLMWZnsFPP

The word list for the positive and negative words are given in <b> positive.txt </b> and <b>negative.txt</b>

## Steps Performed
* Download the data from the above link and unzip it.
* Start the zookeeper service <br>
<b> $KAFKA_HOME/bin/zookeeper-server-start.sh $KAFKA_HOME/config/zookeeper.properties</b>
* Start Kafka service <br>
<b> $KAFKA_HOME/bin/kafka-server-start.sh $KAFKA_HOME/config/server.properties </b>
* Create a topic named twitterstream in kafka <br>
<b> $KAFKA_HOME/bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1   --partitions 1 --topic twitterstream </b>
* Run python <b>twitter_to_kafka.py </b> to stream the tweets and push them to kafka queue
* Run the stream analysis program <br>
<b> $SPARK_HOME/bin/spark-submit --packages org.apache.spark:spark-streaming-kafka-0-8_2.11:2.0.0 twitterStream.py </b>

## Results
Plot of total word counts at each time stamp.

![alt text](https://github.com/kdave97/Twitter-Sentiment-Analytics/blob/master/ans.png)

---- A more detailed explanation about the project is explained in <b>Twitter_Sentiment_Project_Description</b> -----
