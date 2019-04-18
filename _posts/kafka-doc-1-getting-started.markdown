# 1.1 Introduction

## Kafka 是個 Streaming Platform，那是什麼意思?

Streaming Platform的三個關鍵能力

 * 發佈或訂閱 stream，就像傳統的 message queue 或是 enterprise messaging system
 * 可以長久並fault-tolerant地儲存 stream data
 * 當 stream data 到來時，處理 stream

幾個概念

 * Kafka is run as a cluster on one or more servers that can span multiple datacenters.
 * The Kafka cluster stores streams of records in categories called topics.
 * Each record consists of a key, a value, and a timestamp.

四個核心 API

 * Producer API
 * Consumer API
 * Streams API
 * Connector API

## Topics and Logs

Topic: 是一個records的分類，Kafka的topic是能夠有多個訂閱者，也就是可能有0個，1個或多個訂閱者

對於每個 topic，Kafka cluster 是以 partitioned log 的方式儲存 topic

![partitioned log](https://kafka.apache.org/22/images/log_anatomy.png)

在每個 partition 中，records 是被依序地 append 到檔案中，而且不會改變順序 -- 這稱之為 structured commit log

每個存在 partition 中的 record 會被給予一組 id，稱之為 *offset* ，可以用來識別在 partition 中的每個 record
