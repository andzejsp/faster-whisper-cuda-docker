# **A simple, convenient and transparent way to run Wyoming Faster Whisper using a CUDA compatible nvidia GPU.**


## **How to use**

```
git clone https://github.com/Cheerpipe/faster-whisper-cuda-docker
cd faster-whisper-cuda-docker
docker compose up -d
```

## **How to rebuild docker image with the updated dockerfile?**

```
docker compose up --no-deps --build wyoming-whisper-cuda
```

## **Check if GPU is being used:**

```
watch -n0.1 nvidia-smi
```

You should see something like this:

![image](https://github.com/Cheerpipe/faster-whisper-cuda-docker/assets/972765/98cd9518-5044-469d-96b0-d0d083044831)

 
### **For reference keep an eye out for latest whisper python package:**

https://pypi.org/project/wyoming-faster-whisper/

### **For reference keep an eye out for latest cuda runtime:**

https://hub.docker.com/r/nvidia/cuda/tags

### **For reference whisper documentation:**

https://github.com/home-assistant/addons/blob/master/whisper/DOCS.md
