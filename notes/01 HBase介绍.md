# HBase介绍

### 1、关系型数据库与非关系型数据库

##### 		（1）关系型数据库

![关系型数据库](https://github.com/msbbigdata/hbase/blob/master/image/关系型数据库.png)

​				关系型数据库最典型的数据机构是表，由二维表及其之间的联系所组成的一个数据组织

​				优点：

​						1、易于维护：都是使用表结构，格式一致

​						2、使用方便：SQL语言通用，可用于复杂查询

​						3、复杂操作：支持SQL，可用于一个表以及多个表之间非常复杂的查询

​				缺点：

​						1、读写性能比较差，尤其是海量数据的高效率读写

​						2、固定的表结构，灵活度稍欠

​						3、高并发读写需求，传统关系型数据库，硬盘IO是一个很大的瓶颈

##### 		（2）非关系型数据库

![非关系型数据库](https://github.com/msbbigdata/hbase/blob/master/image/非关系型数据库.png)

​				非关系型数据库严格上不是一种数据库，应该是一种数据结构化存储方法的集合，可以是文档或键值对

​				优点：

​						1、格式灵活：存储数据的格式可以是key，value形式、文档形式、图片形式等等，文档形式、图片						形式等等，使用灵活，应用场景广泛，而关系型数据库则只支持基础类型。

​						2、速度快：nosql可以使用硬盘或者随机存储器作为载体，而关系型数据库只能使用硬盘

​						3、高扩展性

​						4、成本低：nosql数据库部署简单，基本都是开源软件

​				缺点：

​						1、不提供sql支持，学习和使用成本较高；

​						2、无事务处理

​						3、数据结构相对复杂，复杂查询方面稍欠

### 2、HBase简介

```
	Use Apache HBase™ when you need random, realtime read/write access to your Big Data. This project's goal is the hosting of very large tables -- billions of rows X millions of columns -- atop clusters of commodity hardware. Apache HBase is an open-source, distributed, versioned, non-relational database modeled after Google's Bigtable: A Distributed Storage System for Structured Data by Chang et al. Just as Bigtable leverages the distributed data storage provided by the Google File System, Apache HBase provides Bigtable-like capabilities on top of Hadoop and HDFS.
```

​		HBase的全称是Hadoop Database,是一个高可靠性，高性能、面向列、可伸缩、实时读写的分布式数据库。

​		利用Hadoop HDFS作为其文件存储系统，利用Hadoop MapReduce来处理HBase中的海量数据，利用Zookeeper作为其分布式协同服务。

​		主要用来存储非结构化和半结构化数据的松散数据（列存NoSQL数据库）。

​		注意：NoSQL的全称是Not Only SQL，泛指非关系型数据库。

### 3、HBase数据模型

![hbase数据模型](https://github.com/msbbigdata/hbase/blob/master/image/hbase数据模型.png)

##### 		1、rowkey

​			（1）决定一行数据，每行记录的唯一标识

​			（2）按照字典序排序

​			（3）RowKey只能存储64K的字节数据					

##### 		2、Column Family & Qualifier

​			（1）HBase表中的每个列都归属于某个列族，列族必须作为表模式(schema)定义的一部分预先给出。如 create ‘test’, ‘course’；

​			（2）列名以列族作为前缀，每个“列族”都可以有多个列成员(column)；如course:math, course:english, 新的列族成员（列）可以随后按需、动态加入；

​			（3）权限控制、存储以及调优都是在列族层面进行的；

​			（4）

##### 		3、TimeStamp时间戳

##### 		4、Cell