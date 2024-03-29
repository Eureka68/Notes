本文章通过循序渐进的方法，讲述了如何构造一个CFT共识协议Paxos。

具体而言就是，Paxos算法分成两个阶段：

1. proposer向超过一半acceptor发送prepare request，其中包含proposal number n。对应的acceptor会检查proposal number n是否大于其所收到的所有prepare request中最大的proposal number latest_n。若大于则将latest_n存储的value（若存在）和latest_n作为response发送给proposer，然后将latest_n更新为n。若小于则发送error给proposer。
2. 如果proposer收到了超过acceptor半数的response，则将向他们再次发送accept request，其中包括了proposal number n和value。其中value的取值为所获得的response中最大latest_n的value。若所有的response都没有value，那么由proposer自行选定value。acceptor将根据收到的accept request是否大于等于latest_n来修改自身存储的value。若大于则修改自身value，若小于则返回error。

Paxos在state machine replication中的应用就是用多个Paxos算法实例来确定state machine commands的执行顺序。

