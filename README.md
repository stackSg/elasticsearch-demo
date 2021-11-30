# ElasticSearch学习

* 结构化数据：表结构
* 非结构化数据：日志
* 半结构化数据：html xml 

# 倒排索引

* 正排(正向)索引

id      content
--------------
1001    my name is zhang san
1002    my name is li si    

keyword     id
---------------
name        1001, 1002
zhang       1001

# 相关概念

* index(索引)-数据库
* Type(类型)-表(7.x中被删除)
* Documents(文档)-行
* Fields(字段)-列

# 相关操作

## 索引操作

1. 创建索引

    PUT http://localhost:9200/shopping
    ```json
    {
        "acknowledged": true,
        "shards_acknowledged": true,
        "index": "shopping"
    }
    ```
    PUT操作具有幂等性
    
2. 获取索引相关信息

    GET http://localhost:9200/shopping
    ```json
    {
        "shopping": {
            "aliases": {},
            "mappings": {},
            "settings": {
                "index": {
                    "creation_date": "1638284162271",
                    "number_of_shards": "1",
                    "number_of_replicas": "1",
                    "uuid": "6_mjUOlmS5u2fwC8T74gMg",
                    "version": {
                        "created": "7070099"
                    },
                    "provided_name": "shopping"
                }
            }
        }
    }
    ```

3. 获取所有索引信息

    GET http://localhost:9200/_cat/indices?v
    ```json
    health status index                    uuid                   pri rep docs.count docs.deleted store.size pri.store.size
    green  open   .kibana_task_manager_1   LSzakcriT1m176C1fPxVew   1   0          2            2     21.1kb         21.1kb
    green  open   .apm-agent-configuration FLrRDS7uTGuRN1T_4NhVcQ   1   0          0            0       208b           208b
    green  open   .kibana_1                mCDJrvMiRQy7KpgyRk6EaQ   1   0         12            5       38kb           38kb
    yellow open   shopping                 6_mjUOlmS5u2fwC8T74gMg   1   1          0            0       208b           208b
    ```
    
4. 删除索引

    DELETE http://localhost:9200/shopping
    ```json
    {
        "acknowledged": true
    }
    ```
    
    