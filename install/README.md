# Run minio sigle node

```
docker-compose.yml
version: '3.5'
services:
  ui:
    image: 'minio/minio:RELEASE.2022-05-26T05-48-41Z'
    environment:
      MINIO_ROOT_USER: xxx
      MINIO_ROOT_PASSWORD: xxx
      MINIO_DOMAIN: xxx
    command: server --console-address ":9001" /data
    restart: always
    volumes:
      - /storage/minio:/data
    ports:
      - '9000:9000'
      - '9001:9001'
```

# Run minio cluster with one node & 2 disk

```
docker-compose.yml
version: '3.8'

services:
  minio:
    image: minio/minio
    container_name: minio
    environment:
      - MINIO_ROOT_USER=xxx
      - MINIO_ROOT_PASSWORD=xxx
    volumes:
      - /data/minio-drive1:/data1
      - /data/minio-drive2:/data2
      #- /data/minio-drive3:/data3
      #- /data/minio-drive4:/data4
    ports:
      - "9000:9000"
      - '9001:9001'
    command: server --console-address ":9001" /data1 /data2
```
