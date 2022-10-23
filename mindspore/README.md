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
