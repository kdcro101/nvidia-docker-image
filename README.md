
# Nvidia CUDA 10 docker image

docker run -d --gpus all --entrypoint /bin/bash nvidia-p37c10 /script/start
docker run --restart unless-stopped -d -h cuda  --gpus all -v projects:/home/dev/projects --name cuda --entrypoint /bin/bash nvidia-p37c10 /script/start

```bash
#!/bin/bash

docker build -t dev-nvidia-p37c10 .

CID=$(docker run -d --gpus all dev-nvidia-p37c10)

echo $CID

docker export $CID > image.tar
cat image.tar | docker import - nvidia-p37c10:latest

# TODO cleanup after..

```
