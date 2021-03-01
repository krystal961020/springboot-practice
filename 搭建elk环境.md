# ELK环境搭建

## 一、ELK概述

### ELK是Elasticsearch+Logstash+Kibana简称

1、Elasticsearch：是一个分布式的搜索和分析引擎，可以用于全文检索、结构化检索和分析，并能将这三者结合起来。Elasticsearch 基于 Lucene 开发，现在是使用最广的开源搜索引擎之一。

2、Logstash： 简单来说就是一根具备实时数据传输能力的管道，负责将数据信息从管道的输入端传输到管道的输出端，与此同时这根管道还可以让你根据自己的需求在中间加上滤网，Logstash提供了很多功能强大的滤网以满足你的各种应用场景。

3、Kibana： 是一个开源的分析与可视化平台，设计出来用于和Elasticsearch一起使用的。你可以用kibana搜索、查看、交互存放在Elasticsearch索引里的数据，使用各种不同的图标、表格、地图等，kibana能够很轻易的展示高级数据分析与可视化。

**ELK实现的日志采集的核心是，通过 logstash 将应用系统的日志通过 input 收集，然后通过内部整理，通过 output 输出到 Elasticsearch 中，其实就是建立了一个 index，然后 kibana作为可视化平台，将 ES 的index进行输出到平台，通过图表的方式进行展示。**

## 二、环境准备

jdk：8

OS：windows

elastsearch：7.11.1

kibana：7.11.1

logstash：7.11.1

springboot：2.4.3

## 三、环境搭建

**elk所有的版本都为统一版本，不能使用不同版本容易出现想象不到的问题！！！！**
![图片](https://github.com/krystal961020/springboot-practice/blob/main/images/elk_version.png)

**因为我是在本地环境搭建的所以很多都比较原生**

1、启动ES服务

![es_start](https://github.com/krystal961020/springboot-practice/blob/main/images/es_start.png)

2、启动kibana服务

![kibana](https://github.com/krystal961020/springboot-practice/blob/main/images/kibana.png)

3、配置logstash，在logstash的config目录下创建test.conf文件并添加相应内容

![test_conf](https://github.com/krystal961020/springboot-practice/blob/main/images/test_conf.png)

![port](https://github.com/krystal961020/springboot-practice/blob/main/images/port.png)

4、配置logback.xml文件

![logback_config](https://github.com/krystal961020/springboot-practice/blob/main/images/logback_config.png)

5、项目添加对应的jar包引用配置，由于用的是gradle所以添加下列信息

![gradle](https://github.com/krystal961020/springboot-practice/blob/main/images/gradle.png)

6、然后启动项目打印的日志就能在kibana上看到了

![result](https://github.com/krystal961020/springboot-practice/blob/main/images/result.png)