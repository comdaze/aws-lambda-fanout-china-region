
在AWS 北京区域创建Kinesis data stream ，名称为：source-bjs-kds；宁夏区域创建创建名称为：target-zhy-kds
(```)
$ git clone https://github.com/comdaze/aws-lambda-fanout-china-region.git
$ cd aws-lambda-fanout-china-region
$ ./fanout deploy --function fanout
$ ./fanout.china register kinesis --function fanout --source-type kinesis --source-arn arn:aws-cn:kinesis:cn-north-1:456370280007:stream/source-bjs-kds --id bjs-zhy-kineis --destination arn:aws-cn:kinesis:cn-northwest-1:456370280007:stream/target-zhy-kds --destination-region cn-northwest-1 --region cn-north-1 --active true
$ ./fanout.china hook --function fanout --source-type kinesis --source source-bjs-kds
$ ./fanout.china list --function fanout --source-type kinesis --source source-bjs-kds
--------------------------------------------------------------
|                            Query                           |
+-----------------+----------+------------------+------------+
|      _1_id      | _2_type  | _3_destination   | _4_active  |
+-----------------+----------+------------------+------------+
|  bjs-zhy-kineis |  kinesis |  target-zhy-kds  |  True      |
+-----------------+----------+------------------+------------+

(```)