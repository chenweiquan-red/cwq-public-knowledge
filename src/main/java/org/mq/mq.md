### 常见问题
    1、为什么使用MQ？
        优点
        ：解耦，不用担心对方的业务是否有异常
        ：异步，多个业务并行处理
        ：削峰，比如请求太多导致业务中断，可以用MQ的拉取消息，在业务的处理范围内即可
        ：小功能，如顺序，存储

        缺点
        ：系统可用性降低，加了个MQ，怎么保证高可用？
        ：系统复杂度高了，加了MQ，顺序消费，重复消费等问题如何保证？
        ：一致性问题，比如A,B,C 三个系统，怎么保证都是处理成功的？

    2、为什么选择RocketMQ?
        : 吞吐量高（十万级）
        ：支持消息堆积10亿，不会因为堆积而导致性能下降
        ：java 开源项目，可以二开
        ：可靠性，0丢失
        
    3、rocketqm集群
        ：NameServer集群，无状态的节点，可集群部署，节点间没有任何信息同步
        ：Broker集群
            ：Broker 分为master 和 slave，一对多
            ：Master 和 Slave 通过指定不同的brokerId区分（相同的brokerName）,ID为0为master
            : ms通常写入数据，sl读取数据

        ：broker和ns是长链接，定时注册toPic到所有的NS中

        

