# Install

- redis.conf: http://download.redis.io/redis-stable/redis.conf
- comment bind 127.0.0.1
- protected-mode no

- docker-compose.yml
```yml
version: '3'

services:
  redis:
    image: redis:5.0.5
    command: redis-server /usr/local/etc/redis/redis.conf
    volumes:
      - ./redis.conf:/usr/local/etc/redis/redis.conf
    ports:
      - "6379:6379"
```

```shell
docker-compose up -d
```

# Test
- https://github.com/caquino/redis-bash
```shell
redis-bash-cli -h localhost SET testkey 1234
redis-bash-cli -h localhost GET testkey
```

# Another Redis Clients
- https://redislabs.com/blog/so-youre-looking-for-the-redis-gui
- https://rdbtools.com/docs/install/linux/
