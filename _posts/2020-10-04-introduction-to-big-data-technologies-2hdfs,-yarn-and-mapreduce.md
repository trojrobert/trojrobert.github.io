---
date: 2020-10-04 04:39:19
layout: post
title: "Introduction to Big Data Technologies 2:HDFS, YARN and MapReduce"
subtitle:
description:
image:
optimized_image:
category:
tags:
author:
paginate: false
---

In my first article in this series [Introduction to Big Data Technologies 1: Hadoop Core Components](https://medium.com/@trojrobert/introduction-to-big-data-technologies-1-hadoop-core-components-9b184d80f87b), I explained what is meant by Big Data, the 5 Vs of Big Data, and brief definitions of all the major components of Hadoop ecosystem.  In this article, we will be diving into 3 backbones of Hadoop which are Hadoop File System(HDFS), Yet Another Resource Negotiator(YARN), and MapReduce. We will also do a hands-on example of MapReduce on the European Football Club Market Value dataset, we will use the concept of MapReduce to find the frequency of the age of players in European football clubs.

![HDFS Architecture](https://res.cloudinary.com/dbzzslryr/image/upload/v1601762689/intro_big_data_2/hdfs_architecture.png "HDFS Architecture")
[source](https://www.edureka.co/blog/apache-hadoop-hdfs-architecture/)

## Hadoop File System(HDFS)

HDFS is the storage layer in Hadoop. It stores large files by splitting them into blocks, each block is stored in a distributed manner, that is on different storage location across a cluster of machines. This helps in analyzing and processing the data quickly. The default block size in Hadoop 2.X is 128MB. Since the different blocks are store parallelly and distributedly, these blocks can also be processed parallelly and distributedly. Each block is replicated to make the system fault tolerance and highly available. Note it is not best for storing small data because it results in a lot of overhead. The major components of HDFS are NameNode and DataNodes. The  DataNodes are stored in racks, distributed systems contain several racks. HDFS has a Master/ Slave Architecture, where the NameNode is the master and the DataNodes are the slaves.
