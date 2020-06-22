### enter commandline of redis in docker
docker exec -it redis1 redis-cli -a cache123

### list all keys
redis-cli KEYS "*"
redis-cli --cluster call localhost:7002 KEYS "*"

### delete all keys from all Redis databases
redis-cli FLUSHALL

### delete all keys of the currently selected Redis database:
redis-cli FLUSHDB

### delete by key pattern
redis-cli KEYS "prefix:*" | xargs redis-cli DEL
/home/appadmin/service/redis/compile/redis/src/redis-cli -p 7001 -a cache123 -c KEYS "prefix:*" |\
  xargs \
  /home/appadmin/service/redis/compile/redis/src/redis-cli -p 7001 -a cache123 -c del
  
/home/appadmin/service/redis/compile/redis/src/redis-cli -p 7001 -a cache123 -c \
  KEYS "{\"TicketDataKey\":{\"ticketId\":\"*\"}}" | xargs \
  /home/appadmin/service/redis/compile/redis/src/redis-cli -p 7001 -a cache123 -c del

### login to your redis inside docker
docker exec -it redis1 bash

### inf of redis (include check key count)
redis-cli info

### [String] set a string
redis-cli SET key value
redis-cli GET key

### [Hash] set a hash 
redis-cli HMSET myhash1 id 1 token abcd
redis-cli HMSET myhash2 id 2 token szy

### [Hash] get all values from the hash key
redis-cli HGETALL myhash1

### [Set] add a set
redis-cli SADD "key" "value"
redis-cli SPOP "key"


### Refernce
- https://redis.io/commands
