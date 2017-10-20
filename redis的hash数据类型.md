## redis的hash数据类型 (2017.10.20)
*存储Hash : String Key 和 String Value的map容器*
1. `启动redis的客户端`
127.0.0.1:6379> 
* galen@galen-virtual:/usr/local/redis$ ./bin/redis-cli   
 
2.`myarr为hash表,其保存的是键值对 这里设置username这个属性的值为galen`
* 127.0.0.1:6379> hset myarr username galen  
(integer) 1
127.0.0.1:6379> hset myarr password 12345
(integer) 1
3. `查看username的属性值`
* 127.0.0.1:6379> hget myarr username
"galen"
4. `查看hash表的所有内容`
* 127.0.0.1:6379> hgetall myarr
1) "username"
2) "galen"
3) "password"
4) "12345"
5. `删除哈希表的某个属性`
127.0.0.1:6379> hdel myarr username
(integer) 1
6. `一次设置多个属性值`
```
127.0.0.1:6379> hmset myarr username password age 23
OK
127.0.0.1:6379> hgetall myarr
1) "username"
2) "password"
3) "age"
4) "23"

127.0.0.1:6379> hget myarr username
"password"

127.0.0.1:6379> hget myarr age
"23"
```
7. `增加值`
```
galen@galen-virtual:/usr/local/redis$ ./bin/redis-cli 
127.0.0.1:6379> hgetall myarr
1) "username"
2) "password"
3) "age"
4) "23"
127.0.0.1:6379> hincrby myarr age 5
(integer) 28
```
8. `判断属性是否存在---hexists`
```
127.0.0.1:6379> hexists myarr username
(integer) 1     //1代表存在

127.0.0.1:6379> hexists myarr username1
(integer) 0    //0代表不存在
```
9. `打印出属性的个数---hlen`
```
127.0.0.1:6379> hlen myarr
(integer) 2
```
10. `得到所有key的名称---hkeys`
```
127.0.0.1:6379> hkeys myarr
1) "username"
2) "age"
```
11. `得到key的所有值---hvals`
```
127.0.0.1:6379> hvals myarr
1) "password"
2) "28"
```
