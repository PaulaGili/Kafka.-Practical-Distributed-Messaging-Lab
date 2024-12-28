# **Kafka. Practical Distributed Messaging Lab** 🚀 

This hands-on lab is designed to provide a deep understanding of **Apache Kafka** by walking through practical exercises. Through these exercises, I learned fundamental Kafka concepts, including creating topics, implementing producers and consumers, managing partitions, and handling offsets. These concepts are essential for working with large-scale data streams in distributed systems.

---

## **General Objective** 🎯

The goal of this project is to provide practical experience with Kafka. Participants will implement a producer and a consumer, work with partitioned topics, and manage offsets. The exercises demonstrate how Kafka processes and transmits data at scale, ensuring high availability, fault tolerance, and scalability in distributed systems.

---

## **Exercises** 📚

### **Exercise 1: Topic Creation** 📝

In this exercise, a basic **topic** is created in Kafka.

1. **Topic name**: The topic is named following the format `<username>Topic`, for example, `paulagiliTopic`.
2. **Number of partitions**: The topic is configured with **1 partition**, meaning all messages will be written to a single partition.
3. **Replication factor**: The **replication factor** is set to 1, meaning there is no redundancy for the topic (no replicas).

#### Steps performed:
- The `--create` command was used to create the topic.
- The existence of the topic was verified using the `--list` command.
- The topic’s details were checked using the `--describe` command, which displays information about the topic, such as the number of partitions and replication factor.

This exercise introduces the creation and management of topics, a foundational concept for using Kafka effectively.

---

### **Exercise 2: Producer and Consumer - Hello World** 🌍

In this exercise, basic interactions between a **producer** and a **consumer** in Kafka are explored.

1. **Producer**:
   - A set of random data is generated following a normal distribution (mean = 0, variance = 1).
   - These random data points are sent to the previously created topic using the Kafka Python client.

2. **Consumer**:
   - A consumer is set up to retrieve messages from the topic.
   - The consumer processes the received data and generates a histogram using the `matplotlib` library to visualize the distribution of the data.

#### Steps performed:
- The producer was configured and run to send data to the created topic.
- The consumer was set up to receive messages from the topic.
- A histogram was generated to visualize the data distribution.

This exercise provides a hands-on understanding of how Kafka producers and consumers work together to send and process messages in Kafka.

---

### **Exercise 3: Using Partitions** 📊

In this exercise, the concept of **partitions** in Kafka is explored to improve scalability and system performance.

1. **Creating a partitioned topic**:
   - The previous topic was deleted, and a new topic was created with **2 partitions**, allowing data to be distributed across multiple partitions, improving scalability.
   - The **replication factor** remains 1 for this topic.

2. **Producer with partitioning logic**:
   - Numbers from 1 to 80 are assigned to partitions based on the following rule:
     - Even numbers go to **partition 0**.
     - Odd numbers go to **partition 1**.
   - The `partition` attribute is used to specify which partition each message should be sent to.

3. **Consumer**:
   - A consumer reads messages from both partitions and verifies that the data is distributed according to the logic defined (even numbers to partition 0, odd numbers to partition 1).

#### Steps performed:
- A topic with multiple partitions was created.
- The producer was configured to send data to specific partitions based on the defined partitioning logic.
- The consumer was configured to read from both partitions and validate the distribution of messages.

This exercise demonstrates how Kafka uses partitions to distribute data across different servers, improving performance and scalability.

---

### **Exercise 4: Managing Offsets** 📌

In this exercise, the concept of **offsets** in Kafka is explored, which helps manage the consumer's position in the message stream.

1. **Querying offsets**:
   - The **current offset** of each partition was queried to understand the position at which the consumer is reading from each partition.

2. **Incrementing offsets**:
   - As new messages were sent to the topic, the **offsets** automatically incremented. Observing this behavior allows for a better understanding of how Kafka tracks message consumption.

3. **Consuming from a specific offset**:
   - A consumer was configured to start reading from a **specific offset**, such as offset 30, allowing for precise control over where message consumption begins.

#### Steps performed:
- The offsets for each partition were queried.
- The consumer observed how offsets increment when new messages are added to the topic.
- The consumer was configured to start consuming messages from a specific offset.

This exercise illustrates the importance of offsets in Kafka, showing how they allow for precise control over the message flow and ensuring that messages are consumed in the correct order.

---

## **Requirements** 🛠️

### **Necessary Software** 💻
- **Apache Kafka**: Distributed messaging platform.
- **Zookeeper**: Required for Kafka coordination.
- **Python 3.x**:
  - Required libraries:
    - `kafka-python`: Kafka client for Python.
    - `numpy`: For generating random data.
    - `matplotlib`: For visualizing data.

### **Environment Setup** 🔧

1. **Install Kafka and Zookeeper**:
   - Follow the official instructions to install and configure Apache Kafka: [Apache Kafka Quickstart](https://kafka.apache.org/quickstart).
   
2. **Install Python dependencies**:
   Execute the following command to install the necessary libraries:
   ```bash
   pip install kafka-python numpy matplotlib
