# Apache-Kafka-Series---Learn-Apache-Kafka-for-Beginners-v3-Notes
This Repository contains my "Apache Kafka Series - Learn Apache Kafka for Beginners v3" Course Notes from Udemy

**I) Kafka Introduction**

**A) Course Introduction**

**B) Apache Kafka in 5 minutes**

**C) Course Objectives**

**D) Welcome! - About your instructor**



# **I) Kafka Introduction**

# **A) Course Introduction**

Hi, this is Stephane Maarek from Conduktor, and welcome to this course in the Apache Kafka series, Kafka for Beginners. This is the third edition of this course, and by this time, the course should be really good for you. Here’s a course introduction, and please don’t skip it, because I’m going to go over some important information.

First of all, welcome to the course. I’m really excited to have you here. By now, over 130,000 students have taken this course, and I’ve received more than 30,000 reviews. I’ve continuously iterated on these reviews over time to keep improving the course. This is an all-new, fresh recording. After all the feedback I received, I wanted to reorganize some lectures, give you more real-life exercises, and provide really cool examples throughout the course. I’ve added new sections and lectures, and the course has been updated to Apache Kafka version 3+, which I believe should also be compatible with Kafka version 4, whenever it comes out. So, happy learning—I hope you’re excited.

Before we continue, just two quick introductions, so please stay here. First, a bit about me so you know who I am. My name is Stephane Maarek, and I will be your teacher for this course. I am the co-founder of a company called Conduktor, which I’ll talk about in the next slide. I’m an online instructor on Apache Kafka and AWS, and I was part of the Program Committee of Kafka Summit in 2019 and 2020, which is the major Kafka conference worldwide. I’ve created many courses on Apache Kafka, which I call the Apache Kafka Series, and I’ve written blogs for Confluent, Medium, and other platforms. You can also find me on GitHub, LinkedIn, Medium, Twitter, and Instagram if you’d like to follow me on your preferred platform.

Now, a short introduction to Conduktor. What is Conduktor? It’s a company that I co-founded to make Apache Kafka accessible to everyone, including you. We built a graphical user interface with many features for Kafka and its entire ecosystem. The goal was to create a complete system that makes Apache Kafka enterprise-ready, so we added many advanced features on top of it. In the context of this course, we’ll be using the UI. You’ll also get a free Kafka personal cluster that you can use as you like, and you can even get a free organization cluster to collaborate with your colleagues if you want to. Conduktor supports any Kafka cluster, all security mechanisms, and connects to nearly everything in the Kafka ecosystem. This will help you learn Apache Kafka, and it will also help you work faster and more efficiently after you’ve completed this course.

That’s it for this lecture. I hope you liked it, and I’ll see you in the next lecture.

# **B) Apache Kafka in 5 minutes**

Hi, this is Stephane from Conduktor, and welcome to this lecture in which I’m going to introduce Kafka to you. Let’s start by looking at the challenges companies face when it comes to data integration.

In a typical company, you’ll have a source system, for example a database. At some point, another part of the company will want to take that data and move it into another system, known as a target system. This means the data has to move from the source system to the target system. Initially, this seems very simple: someone writes some code to extract the data, transform it, and then load it into the target system.

However, as the company grows, things become more complex. The company now has many source systems and many target systems. As a result, the data integration challenge becomes much harder, because all the source systems must send data to all the target systems to share information. This leads to a large number of integrations. For example, if you have four source systems and six target systems, you would need to write 24 separate integrations to make everything work.

Each of these integrations introduces additional complexity. There are challenges related to protocols, because different technologies might be used, such as TCP, HTTP, REST, FTP, or JDBC. There are also challenges around data formats, such as whether the data is binary, CSV, JSON, Avro, or Protobuf. On top of that, there are issues related to data schemas and schema evolution, especially when the structure of the data changes in the source or target systems. Finally, each source system experiences increased load because it has to manage many connections and requests to extract and send data.

So how do we solve this problem? We introduce decoupling using Apache Kafka. In this architecture, we still have our source systems and our target systems, but Apache Kafka sits in the middle. The source systems are now responsible for producing data into Apache Kafka. Kafka then holds a continuous data stream containing data from all the source systems.

If target systems need data from the source systems, they no longer connect directly to them. Instead, they consume data from Apache Kafka. Kafka is designed to both receive and send data efficiently, which makes the overall system more scalable and easier to manage.

To make this more concrete, source systems could include website events, pricing data, financial transactions, or user interactions. All of these generate data streams in real time, which are sent to Apache Kafka. Target systems could include databases, analytics systems, email systems, or audit systems. This is the type of architecture we’ll be implementing.

Now, why is Apache Kafka so powerful? Kafka was originally created at LinkedIn and later released as an open-source project. Today, it is mainly maintained by large organizations such as Confluent, IBM, Cloudera, LinkedIn, and others. Kafka is distributed, resilient, and fault-tolerant, meaning you can perform upgrades and maintenance without taking the entire system down.

Kafka also supports horizontal scalability, which means you can add more brokers to your Kafka cluster over time and scale to hundreds of brokers. It is capable of handling extremely high message throughput, reaching millions of messages per second, as seen in companies like Twitter. Kafka is also highly performant, with very low latency—sometimes under 10 milliseconds—which is why it’s considered a real-time system.

Apache Kafka has been widely adopted across the world. Over 2,000 companies publicly use Kafka, and around 80% of Fortune 100 companies rely on it. Well-known users include LinkedIn, Airbnb, Netflix, Uber, and Walmart. That said, you don’t need to be a massive corporation to benefit from Apache Kafka.

In terms of use cases, Kafka is commonly used as a messaging system and an activity tracking system. It’s used to gather metrics from different locations and to collect application logs—some of the earliest Kafka use cases. More recently, Kafka has become a key tool for stream processing, for example using the Kafka Streams API. It is also widely used to decouple system dependencies and microservices, and it integrates well with big data technologies such as Spark, Flink, Storm, and Hadoop. Kafka is also heavily used for publish-subscribe communication in microservices architectures.

Looking at real-world examples, Netflix uses Apache Kafka to apply recommendations in real time while you’re watching TV shows. Uber uses Kafka to collect user, taxi, and trip data in real time to forecast demand and calculate pricing dynamically. LinkedIn uses Kafka to prevent spam, collect user interactions, and generate better connection recommendations in real time.

In all these scenarios, Kafka acts as the transportation mechanism that enables massive data flows across an organization. By now, you should have a good understanding of what Kafka is, how it is used, and why it was created.

# **C) Course Objectives**

Hi, this is Stephane from Conduktor. In this lecture, I’ll give you an overview of what you’ll be learning in this course and how the course is structured.

We’ll start with the Kafka theory section, where you’ll learn about Kafka clusters and Kafka brokers. You’ll understand Kafka producers and how they take data from source systems into the Kafka cluster. You’ll also learn about Kafka consumers and how they take data from the cluster and send it to target systems. In addition, we’ll cover how Kafka is managed, either using ZooKeeper or, more recently, using Kafka KRaft mode.

In this course, you’ll also get an introduction to Conduktor, where you’ll see how to start Kafka and interact with it using a graphical user interface. We’ll introduce Kafka Connect, Kafka Streams, and the Confluent Schema Registry. You’ll learn how Kafka is used in enterprise environments, explore Kafka architectures, and review real-world use cases. We’ll also cover advanced APIs, topic configurations, and many additional concepts.

The course is structured into multiple parts. Part One focuses on the fundamentals and contains about four hours of content. In this part, I’ll walk you through Kafka theory end to end so you fully understand what Kafka is all about. After that, we’ll start Kafka on your local machine, with different instructions provided for Linux, Windows, and macOS. You’ll then use the Kafka command-line interface to interact with Kafka from the terminal, and finally, we’ll write Java programs to start coding against Kafka.

Next, we’ll move on to real-world architectures. Here, we’ll build a more complex Java producer, specifically a Wikimedia producer, and a more complex Java consumer, the OpenSearch consumer. After that, we’ll explore the extended APIs, including Kafka Connect, Kafka Streams, and Schema Registry. We’ll also review case studies and see how Kafka is used in enterprise settings. Finally, Part Three will focus on advanced topic configurations and any other advanced lectures included in the course.

This is a beginner’s course, and you do not need any prior knowledge of Kafka. However, you should be comfortable using the command line. I will go slowly, but it’s helpful if you’ve already used a terminal on your computer. We’ll also do some Java programming, so having basic knowledge of Java or programming in general is beneficial. We’ll use Java 11, but even if you don’t know Java, that’s fine—you can download the code and follow along, especially when we discuss Kafka configurations. Linux and macOS are strongly preferred, but if you’re using Windows, I’ll explain the caveats and provide appropriate instructions. Most importantly, you need to be willing to learn a new and powerful technology—and if you’re here, that means you are.

So, who is this course for? You might be a developer who wants to learn how to write and run applications that leverage Kafka. You might be an architect who wants to understand Kafka’s role in the enterprise data pipeline. Or you might be in DevOps, wanting to understand how Kafka works with topic partitions and multi-broker setups.

Welcome to the Apache Kafka Series. You’re currently in Volume One: Kafka for Beginners, which will give you a strong foundation in Kafka, teach you basic operations, and help you write your first producers and consumers. Topics such as Kafka Connect, Kafka Streams, ksqlDB, Confluent components, Kafka security, Kafka monitoring and operations, and Kafka cluster setup and administration are part of other courses in the series and not covered here. If you’re preparing for certifications, there are also the Confluent Certification for Developers and the Confluent Certification for Operators.

Many people ask in which order they should take the courses and whether this course is enough. Kafka for Beginners should always be your first course. It is comprehensive and sufficient to give you a solid understanding of Kafka. If you want to specialize as a developer, courses on Kafka Connect, Kafka Streams, ksqlDB, and Confluent components are essential. If you want to specialize as an administrator, Kafka security, Kafka monitoring, and Kafka cluster setup will be your best options.

# **D) Welcome! - About your instructor**

Hi, and welcome. My name is Stephane Maarek, and I will be your instructor for this course. I’m delighted to have you here, and I truly hope that you enjoy the course and go all the way through it. This is just a short, two-minute introduction so you can get to know me, and then we’ll jump right into the course.

I’m French, so if you notice a slight accent, that’s where it comes from—the wonderful country of France. Over the years, I’ve also lived in the United States, Australia, Mexico, and now Portugal. My expertise is mainly focused on AWS certifications and Apache Kafka. This comes from my professional background, where I’ve worked as a data analyst, a big data engineer, a developer, and an AWS solutions architect. And today—well—I’m a teacher. Teaching is my passion, and I truly love helping people achieve their goals through online learning.

Before we get started with the course, there are two main ways you can connect with me. The first is LinkedIn, where I share professional updates such as news about the AWS and Kafka ecosystems, new course releases, and, most importantly, where I congratulate students on their achievements. If you complete a course or pass a certification, feel free to make a post and tag me—I’ll make sure to congratulate you. Seeing my students succeed and reach their goals is my biggest motivation.

The second way to connect with me is Instagram, which is a personal project I started over two years ago. I love traveling the world, and I decided to meet students along the way. Whenever I visit a new destination, I make a post and try to meet students in that location. So far, I’ve already met over 25 students. When I meet students, we talk about their goals, how the course is helping them, their achievements, and their careers. Afterward, I usually make a post about the experience. If you’d like a chance to meet me, read other students’ stories, or get more personal behind-the-scenes updates, you can follow me on Instagram.

Finally, before you begin this course, I want you to set a goal. Setting a goal greatly increases your chances of finishing the course and learning effectively. For example, you might decide to complete the course in three weeks—that’s a great goal. Take a piece of paper and a pen, write your goal down, and commit to it. This approach will help you stay focused and get the most value out of the course.

Don’t hesitate to go through the lectures as many times as you need—that’s exactly what video learning is for. If it helps, you can also adjust the playback speed, either speeding it up or slowing it down, so it’s easier for you to understand me.

That’s it for me. I hope you enjoy this course, and I’ll see you in the next lecture. Happy learning.
