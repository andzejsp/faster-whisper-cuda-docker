# **A simple, convenient and transparent way to run Wyoming Faster Whisper using a CUDA compatible nvidia GPU.**

## **How to use**

```
git clone https://github.com/andzejsp/faster-whisper-cuda-docker
```
```
cd faster-whisper-cuda-docker
```
```
docker compose up -d
```

docker-compose.yaml
```yaml
services:
  wyoming-whisper-cuda:
    container_name: wyoming-whisper-cuda
    build:
      context: ./docker/cuda
      dockerfile: Dockerfile    
    command: --model medium-int8 --language en --beam-size 5
    volumes:
      - /path/to/your/data/directory:/data
    restart: unless-stopped
    ports:
      - 10300:10300
    runtime: nvidia
    deploy:
        resources:
          reservations:
            devices:
              - driver: nvidia
                count: 1
                capabilities: [gpu]
```

### **If you have problems with nvidia runtime or something, try installing nvidia container tools:**
You must also use nvidia drivers - the official ones.

https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html


## **Check if GPU is being used:**

```
watch -n0.1 nvidia-smi
```

You should see something like this:

![image](https://github.com/Cheerpipe/faster-whisper-cuda-docker/assets/972765/98cd9518-5044-469d-96b0-d0d083044831)

 
### **For reference keep an eye out for latest whisper python package:**
Edit docker/cuda/Dockerfile if needed

https://pypi.org/project/wyoming-faster-whisper/

### **For reference keep an eye out for latest cuda runtime:**
Edit docker/cuda/Dockerfile if needed

https://hub.docker.com/r/nvidia/cuda/tags

### **For reference whisper documentation:**

https://github.com/home-assistant/addons/blob/master/whisper/DOCS.md

## **How to rebuild docker image with the updated dockerfile?**

```
docker compose up --no-deps --build wyoming-whisper-cuda
```
