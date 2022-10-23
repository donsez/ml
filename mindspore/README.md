# MindSpore

MindSpore is a new open source deep learning training/inference framework that could be used for mobile, edge and cloud scenarios developed by Haiwei.

https://github.com/mindspore-ai/mindspore/blob/master/README.md

## Using MindSpore with Docker

Several images of MindSpore containers are available on [Docker Hub](https://hub.docker.com/search?q=mindspore).

For Mac Silicon (M1 and M2), pull the image for `cpu-aarch64`.

```bash
docker pull mindspore/mindspore-cpu-aarch64:1.0.0
```

```bash
docker run --name mindspore --hostname mindspore -it -v `pwd`:/work mindspore/mindspore-cpu-aarch64:1.0.0 /bin/bash
```

Run the `mul.py` Python script:
```bash
root@mindspore:/# cd /work
root@mindspore:/work# ls
README.md  mul.py
root@mindspore:/work# python mul.py
[ 4. 10. 18.]
```


You can also nvoke directly the `mul.py` Python script with:
```bash
docker run -t --rm -v `pwd`:/work mindspore/mindspore-cpu-aarch64:1.0.0 python /work/mul.py
```

## Build the latest stable version of the docker image

Dockerfile files are available [here for CPU](https://github.com/mindspore-ai/mindspore/tree/master/scripts/docker/mindspore-cpu) and [here for GPU](https://github.com/mindspore-ai/mindspore/tree/master/scripts/docker/mindspore-gpu).

```bash
wget https://raw.githubusercontent.com/mindspore-ai/mindspore/master/scripts/docker/mindspore-cpu/1.9.0/Dockerfile
docker image build --tag mindspore/mindspore-cpu-aarch64:1.9.0 .
docker tags 
```

It it failed
```
[+] Building 167.6s (13/13) FINISHED                                            
 => [internal] load build definition from Dockerfile                       0.0s
 => => transferring dockerfile: 2.57kB                                     0.0s
 => [internal] load .dockerignore                                          0.0s
 => => transferring context: 2B                                            0.0s
 => [internal] load metadata for docker.io/library/ubuntu:18.04            2.4s
 => [auth] library/ubuntu:pull token for registry-1.docker.io              0.0s
 => [1/9] FROM docker.io/library/ubuntu:18.04@sha256:40b84b75884ff39e4cac  5.7s
 => => resolve docker.io/library/ubuntu:18.04@sha256:40b84b75884ff39e4cac  0.0s
 => => sha256:0e9b69cf8198dafe5b7db1eee7b96b96238f8346e 23.73MB / 23.73MB  4.5s
 => => sha256:40b84b75884ff39e4cac4bf62cb9678227b1fbf9dbe 1.41kB / 1.41kB  0.0s
 => => sha256:354437aa4d06f7d91cf3ddcd97efac9d9cf746c8b9b0071 529B / 529B  0.0s
 => => sha256:7613777544784a5c0496fb94beaa478ca1de1ea8060 1.48kB / 1.48kB  0.0s
 => => extracting sha256:0e9b69cf8198dafe5b7db1eee7b96b96238f8346ec641dd4  1.0s
 => [2/9] RUN apt update     && DEBIAN_FRONTEND=noninteractive apt insta  24.0s
 => [3/9] RUN DEBIAN_FRONTEND=noninteractive apt install -y     gcc       13.8s
 => [4/9] RUN DEBIAN_FRONTEND=noninteractive apt install -y     libnuma-d  1.7s 
 => [5/9] RUN echo "dash dash/sh boolean false" | debconf-set-selections   0.4s 
 => [6/9] RUN DEBIAN_FRONTEND=noninteractive dpkg-reconfigure dash         0.4s 
 => [7/9] RUN apt install -y libffi-dev libssl-dev zlib1g-dev libbz2-de  114.4s 
 => [8/9] RUN mkdir -pv /root/.pip     && echo "[global]" > /root/.pip/pi  4.0s 
 => ERROR [9/9] RUN pip install --no-cache-dir https://ms-release.obs.cn-  0.7s 
------                                                                          
 > [9/9] RUN pip install --no-cache-dir https://ms-release.obs.cn-north-4.myhuaweicloud.com/1.9.0/MindSpore/cpu/x86_64/mindspore-1.9.0-cp37-cp37m-linux_x86_64.whl     && pip install --no-cache-dir https://ms-release.obs.cn-north-4.myhuaweicloud.com/1.9.0/MindInsight/any/mindinsight-1.9.0-py3-none-any.whl:
#13 0.503 Looking in indexes: http://mirrors.aliyun.com/pypi/simple/
#13 0.506 ERROR: mindspore-1.9.0-cp37-cp37m-linux_x86_64.whl is not a supported wheel on this platform.
------
executor failed running [/bin/sh -c pip install --no-cache-dir https://ms-release.obs.cn-north-4.myhuaweicloud.com/1.9.0/MindSpore/cpu/x86_64/mindspore-1.9.0-cp37-cp37m-linux_x86_64.whl     && pip install --no-cache-dir https://ms-release.obs.cn-north-4.myhuaweicloud.com/1.9.0/MindInsight/any/mindinsight-1.9.0-py3-none-any.whl]: exit code: 1
```

https://github.com/mindspore-ai/mindspore/issues/171