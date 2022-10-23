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

List the [versions of the mindspore python packages for `aarch64` and `CPU`](https://www.mindspore.cn/install/en)

```bash
VERSION=1.8.0
wget https://raw.githubusercontent.com/mindspore-ai/mindspore/master/scripts/docker/mindspore-cpu/$VERSION/Dockerfile
```

Edit `Dockerfile` for replacing the 1.8.1 python packages
* https://ms-release.obs.cn-north-4.myhuaweicloud.com/1.8.1/MindSpore/cpu/aarch64/mindspore-1.8.1-cp37-cp37m-linux_aarch64.whl


```bash
VERSION=1.8.1
ARCH=aarch64
docker image build --tag mindspore/mindspore-cpu-$ARCH:$VERSION .
docker tag mindspore/mindspore-cpu-$ARCH:$VERSION mindspore/mindspore-cpu-$ARCH:latest
docker images | grep  mindspore
```

Now, you can also test the brand-new image with:
```bash
docker run -t --rm -v `pwd`:/work mindspore/mindspore-cpu-aarch64:latest pip show mindspore mindinsight
docker run -t --rm -v `pwd`:/work --workdir=/work mindspore/mindspore-cpu-aarch64:latest python mul.py
docker run -t --rm -v `pwd`:/work --workdir=/work mindspore/mindspore-cpu-aarch64:latest python tensor.py
docker run -t --rm -v `pwd`:/work --workdir=/work mindspore/mindspore-cpu-aarch64:latest python add.py
```


## Installing MindSpore in CPU by pip-macOS (and others)

https://www.mindspore.cn/install/en

