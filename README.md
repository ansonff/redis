### Install

- redis.conf: http://download.redis.io/redis-stable/redis.conf
- comment bind 127.0.0.1
- protected-mode no

- docker-compose.yml
```yaml
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
- Start
```console
docker-compose up -d
```

### Test
- https://github.com/caquino/redis-bash
```console
redis-bash-cli -h localhost SET testkey 1234
redis-bash-cli -h localhost GET testkey
```

### Build your own redis image
```console
docker build -t my-redis . --no-cache
```

### Another Redis Clients
- https://redislabs.com/blog/so-youre-looking-for-the-redis-gui
- https://rdbtools.com/docs/install/linux/
