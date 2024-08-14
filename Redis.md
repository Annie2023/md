# Redis

## 字符串：string

SET name value

GET name

DELETE name

EXISITS *

KEYS *

FLUSHALL

区分大小写

默认字符串存储数据，二进制安全，不支持中文

 中文显示：redis-cli --raw

TTL name

EXPIRE name 10（time）

SETEX name 5

SETNX name 5：键不存在起作用



## list（可重复）

LPUSH/RPUSH（头/尾）  letter a

LPOP/RPOP

LLEN

LRANGE letter 0 -1 ：获取列表中所有元素

LTRIM letter 1 3：只保留命令中start和stop的命令



## set（不可重复）

SADD course Redis

SMEMBERS course:查看当前成员

SISMEMBER course Redis：判断

SREM course Redis：删除

SINTER。。。。运算



## SortedSet(成员唯一，分数可重复)

ZADD result  682 清华 660 北大

ZRANG result 0 -1 WITHSCORES

ZSCORE result 清华

ZRANK result 清华

ZREVRANK result 清华

ZREM result 清华



## Hash

HSET key value

HGET person key

HGETALL person

HDEL 

HEXISTS

HKEYS

HLEN



## 发布订阅功能

publish

subscribe



## stream

XRANGE - +：开始和结束

XTRIM geekhour maxlength  0：0表示全部删除

 XADD geekhour 1-0 course git

XREAD COUNT 2 BLOCK 1000 STREAMS geekhour 0：读取两条消息没读取到阻塞1000毫秒0表示从头开始读

XGROUP CREATE geekhour group1 0：创建消费者组

XINFO GROUPS geekhour :查看组

XGROUP CREATCONSUMER geekhour group1 consumer

XREADGROUP GROUP group1 consumer1 COUNT 2 BLOCK 3000 STREAMS geekhour >



## Geospatial

GEO  

GEOPOS city beijing

GEODIST city beijing shanghai km

GEOSEARCH city FROMMEBER shanghai BYRADIUS 1000 km



## HyperLogLog

基数（统计工作）

PF

PFADD course git

PFCOUNT course

PFMERGE



## bitmap

offset

setbit

getbit

SET dianzan “\xF0”

BITCOUNT

BITPOS dianzan 0：第一个出现0的位置



## bitfield

BITFIELD player：1 set u8 #0 1

GET  player:1

 BITFIELD player :1 set u32 #1 100

 BITFIELD player :1 get u32 #1

 BITFIELD player :1 incrby u32 #1 100：增加100



## 事务

不同于mysql，一个不成功全不成功

可部分成功

MULTI（放入缓存队列）

- SET
- LPUSH
- SADD

EXEC/DISCARD（结束事务提交）



## Redis持久化

RDB（REDIS Database）

AOF



## 主从复制

修改配置文件

cd /opt/homebrew/etc



## 哨兵模式

监视节点

自动故障转移

vi sentinel.conf

sentinel monitor master 1270.0.1 6379 1

redis-sentinel sentinel.conf

info replication







