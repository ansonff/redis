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
