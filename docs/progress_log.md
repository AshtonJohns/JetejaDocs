# Using tensorflow

## Workstation (Ubuntu 20.04, 5950X, rtx3080)

### Install CUDA Toolkit
https://developer.nvidia.com/cuda-downloads

These were my options: 
* Operating System: Linux
* Architecture: x86_64
* Distribution: Ubuntu 20.04
* Version: Latest (e.g., CUDA 12.0)

### Add CUDA paths
```bash
echo 'export PATH=/usr/local/cuda/bin:$PATH' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc
```

### Verify installation
```bash
nvcc --version
```

## Install cuDNN
https://developer.nvidia.com/cudnn

Verify your options

## Training and optimizing

### Install requirements.txt
```bash
cd ~/jeteja_robot
pip install -r requirements.txt
```

### Install python virtual environment
```bash
sudo apt install -y python3-venv
```

### Create the virtual environment
```bash
python3 -m venv tf-gpu
source tf-gpu/bin/activate
```

### Verify TensorFlow and GPU support
```bash
python -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"
```

## Jetson Orin Nano (Jetpack 5.1.3)

## Install tensorflow 
[https://docs.nvidia.com/deeplearning/frameworks/install-tf-jetson-platform/index.html](https://docs.nvidia.com/deeplearning/frameworks/install-tf-jetson-platform/index.html)

## Possible issue fixes
### Set OpenMP Environment Variable
```bash
export LD_PRELOAD=/usr/lib/aarch64-linux-gnu/libgomp.so.1
```

### Enable TensorFlow’s cuda_malloc_async Allocator

```bash
export TF_GPU_ALLOCATOR=cuda_malloc_async

```


# Copying from jetson to powerful computer

## Rsync

```bash
rsync -avz [source-username]@[source-IP]:/path/to/source/ /path/to/destination/
```