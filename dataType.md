# String
```
127.0.0.1:637> SET lecture redis-cache
OK

127.0.0.1:637> GET lecture
"redis-cache"
```
<br>

```
127.0.0.1:637> MSET price 100 language ko
OK

127.0.0.1:637> MGET lecture price language
1) "redis-cache"
2) "100"
3) "ko"
```
**MSET (Multi set) / MGET (Multi get)**<br>
다수의 string 한번에 저장, 조회
<br><br>

```
127.0.0.1:637> INCR price
(integer) 101

127.0.0.1:637> INCRBY price 0
(integer) 110

127.0.0.1:637> MGET lecture price language
1) "redis-cache"
2) "110"
3) "ko"
```
별도의 integer 타입은 없고, 숫자도 string 으로 저장 됨<br><br>


```
127.0.0.1:637> SET redis-cache '{"price": 100, "language": "ko"}'
OK

127.0.0.1:637> GET redis-cache
"{\"price\": 100, \"language\": \"ko\"}"

127.0.0.1:637> SET redis-cache:ko:price 200
OK

127.0.0.1:637> GET redis-cache:ko:price
"200"
```
Naming convention: key 를 만들때 **":"** 를 사용해서 의미단위로 구분
<br><br>

# List (Doubly Linked List)
각 노드가 이전 노드와 다음 노드를 가리키는 포인터를 가짐 (push/pop 에 최적화 O1)
<br><br>
### Queue
```
127.0.0.1:6379> LPUSH queue job1 job2 job3
(integer) 3

127.0.0.1:6379> RPOP queue
"job1"
```
### Stack
```
127.0.0.1:6379> LPUSH stack job1 job2 job3
(integer) 3

127.0.0.1:6379> LPOP stack
"job3"
```