> # Kafka Docker

### Start the servers:
```shell
docker compose up -d --build
```

### Check the logs:
```shell
docker container logs kafka-writer
docker container logs kafka-reader
```

### Shut down servers:
```shell
docker compose down
```

### View a list of all containers:
```shell
docker images
```

### Cleaning up junk containers that have piled up:
```shell
docker image prune -f
```

### Enable autostart service always
```shell
docker update --restart=always kafka-writer
docker update --restart=always kafka-reader
```

### Disable autostart service always
```shell
docker update --restart=no kafka-writer
docker update --restart=no kafka-reader
```
