## redis的string数据类型 (2017.10.20)

1. `设置数字---增加`
```
127.0.0.1:6379> incr num1     //如果我们之前没有定义过num1,则默认为0
(integer) 1

127.0.0.1:6379> get num1      //查看 num1
"1"

127.0.0.1:6379> incr num1     //在num1=1的基础上加1,即 num1 = num1 + 1
(integer) 2

127.0.0.1:6379> get num1      //查看 num1
"2"

127.0.0.1:6379> incrby num1 6 //增加6
(integer) 8
```
2. `设置数字---减少`
```
galen@galen-virtual:/usr/local/redis$ ./bin/redis-cli 
127.0.0.1:6379> decr num2     //如果我们之前没有定义过num1,则默认为0
(integer) -1
127.0.0.1:6379> decr num2
(integer) -2
127.0.0.1:6379> decrby num2 5
(integer) -7
```
3. `字符串扩展`
```
127.0.0.1:6379> set book 1
OK
127.0.0.1:6379> get book
"1"
127.0.0.1:6379> append book 5     //在字符串"1"的后面添加字符串"5",即现在的字符串变为"15"
(integer) 2                       //这里的2表示字符串的字符个数为2
127.0.0.1:6379> get book
"15"
127.0.0.1:6379> append book 678
(integer) 5                       //字符串中的字符个数为5
127.0.0.1:6379> get book
"15678"
```