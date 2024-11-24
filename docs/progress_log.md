# Using tensorflow

### Pull the NVIDIA Docker Image for TensorFlow + ML
```bash
docker pull nvcr.io/nvidia/l4t-ml:r35.2.1-py3
```

### Run the Docker Container
```bash
docker run --runtime nvidia -it --rm \
    -v /path/to/your/ros/workspace:/workspace \
    nvcr.io/nvidia/l4t-ml:r35.2.1-py3
```

### Run the Docker Container and set working directory
```bash
docker run --runtime nvidia -it --rm \
    -v ~/jeteja_robot:/workspace \
    -w /workspace \
    nvcr.io/nvidia/l4t-ml:r35.2.1-py3
```

## Possible issue fixes
### Set OpenMP Environment Variable
```bash
export LD_PRELOAD=/usr/lib/aarch64-linux-gnu/libgomp.so.1
```

## Enable TensorFlow’s cuda_malloc_async Allocator

```bash
export TF_GPU_ALLOCATOR=cuda_malloc_async

```


