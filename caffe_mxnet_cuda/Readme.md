# CUDA-enabled Deep Learning Image

Jupyter notebook server (port 8888) for deep learning.  Contains:

- Caffe + CUDNN
- Theano (no CUDNN)
- MXnet
- Keras
- Lasagne
- Scikit-learn
- Jupyter

The github repo and docker image are both `henryzlo/deepdock`

Requirements
------------

You will need CUDA 7.5 installed and a GPU.  Then you need to attach the GPU to the image with the flags:

```
--device /dev/nvidia0 --device /dev/nvidia-uvm --/device /dev/nvidiactl
```

Cheatsheet
----------

Usually I have a `data` and `workspace` folder that I like to attach.  This can be done using the flags:

```
-v `pwd`/workspace:/root/workspace -v `pwd`/data:/root/data
```

Putting it all together:

```
docker run -it -P \
  --device /dev/nvidia0 --device /dev/nvidia-uvm --device /dev/nvidiactl \
  -v `pwd`/workspace:/root/workspace -v `pwd`/data:/root/data henryzlo/deepdock
```

If you want a shell in the image, run the command above, then use:
```
docker exec -it <image-name> bash
```
Where `<image-name>` can be obtained via `docker ps`.

To connect to the notebook server, point browser to `<IP>:8888`, where `<IP>` can be obtained via `docker inspect <image-name> | grep IPAddress`

Default password is `abc123ak47`
