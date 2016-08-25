
## 日志收集分析平台

### 架构

日志收集分析平台的拓扑：

![Image](https://raw.githubusercontent.com/buzzerbeat/ELKDeploy/master/arch.png)

1. 使用一台Nginx代理访问kibana的请求;
2. 一台es组成es集群，上面都安装kibana;（以下对elasticsearch简称es）
3. 中间件就是kafka集群，作为消息中间件;
4. 线上服务器使用logstash收集日志
5. 简化起见，1-3均部署在一台机器上



### 组件

#### ElasticSearch+Logstash+Kibana（ELK）

##### ElasticSearch介绍

Elasticsearch是一个基于Apache Lucene(TM)的开源搜索引擎。无论在开源还是专有领域，Lucene可以被认为是迄今为止最先进、性能最好的、功能最全的搜索引擎库。

但是，Lucene只是一个库。想要使用它，你必须使用Java来作为开发语言并将其直接集成到你的应用中，更糟糕的是，Lucene非常复杂，你需要深入了解检索的相关知识来理解它是如何工作的。

Elasticsearch也使用Java开发并使用Lucene作为其核心来实现所有索引和搜索的功能，但是它的目的是通过简单的RESTful API来隐藏Lucene的复杂性，从而让全文搜索变得简单。

不过，Elasticsearch不仅仅是Lucene和全文搜索，我们还能这样去描述它：

* 分布式的实时文件存储，每个字段都被索引并可被搜索
* 分布式的实时分析搜索引擎
* 可以扩展到上百台服务器，处理PB级结构化或非结构化数据
 
而且，所有的这些功能被集成到一个服务里面，你的应用可以通过简单的RESTful API、各种语言的客户端甚至命令行与之交互。

##### Logstash介绍

Logstash是一个开源的具有实时pipelining功能的日志收集引擎。Logstash可以将不同的源数据动态组织成统一的形式。通过编写input，filter，output插件的规则来实现日志的组织和转换。


Logstash特性如下：

* 整合Es和其他output
* 插件化的pipline架构
* 社区可扩展性和面向开发者的插件生态系统

![Image](https://www.elastic.co/guide/en/logstash/2.3/static/images/logstash.png)


##### Kibana介绍


Kibana 是一个使用 Apache 开源协议，基于浏览器的 Elasticsearch 分析和搜索仪表板。Kibana 非常容易安装和使用。整个项目都是用 HTML 和 Javascript 写的，所以 Kibana 不需要任何服务器端组件，一个纯文本发布服务器就够了。Kibana 和 Elasticsearch 一样，力争>成为极易上手，但同样灵活而强大的软件。

![Image](http://7xiys0.com1.z0.glb.clouddn.com/gitbook143110444247.jpg)


##### ELK安装&运行&配置


[Ubuntu环境下安装](https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elk-stack-on-ubuntu-14-04)


#### 使用ELK 采集nginx日志


http://blog.arganzheng.me/posts/use-logstash-to-collect-nginx-access-log.html

### 引用

[官方文档_英文](https://www.elastic.co/guide/en/elasticsearch/reference/current/getting-started.html)
