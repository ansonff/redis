# Install
- docker-compose.yml
````yml
version: '3'
services:
  redis:
    image: redis:5.0.5
    ports:
      - "6379:6379"
```

```bash
docker-compose up -d
```
