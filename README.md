## Openrelik worker for interacting with a Bulkextractor

### Installation
Add to your docker-compose configuration:

```
  openrelik-worker-bulkextractor:
    container_name: openrelik-worker-bulkextractor
    image: ghcr.io/openrelik/openrelik-worker-bulkextractor
    restart: always
    environment:
      - REDIS_URL=redis://openrelik-redis:6379
    volumes:
      - ./data:/usr/share/openrelik/data
    command: "celery --app=src.app worker --task-events --concurrency=1 --loglevel=INFO -Q openrelik-worker-bulkextractor"
```
