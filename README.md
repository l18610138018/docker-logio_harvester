# logio harvester

## Installation
### Step 1 Installation

```
docker pull maltyxx/logio_harvester
```

### Step 2 Run

```
docker run -ti --name logio_harvester maltyxx/logio_harvester
```

### Step 3 Compose

```yaml
logio_harvester:
    image: maltyxx/logio_harvester
    environment:
        - TZ=Europe/Paris
    restart: always
```
### Step 4 Compose combined

```yaml
logio_harvester:
    image: maltyxx/logio_harvester
    links:
        - logio_server
    environment:
        - TZ=Europe/Paris
    volumes:
        - /var/log/apache/access.log:/var/log/docker/access.log:ro

logio_server:
    image: maltyxx/logio_server
    ports:
        - "28777"
        - "28778:28778"
    environment:
        - TZ=Europe/Paris
```