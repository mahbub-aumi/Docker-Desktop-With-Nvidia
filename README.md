# Docker-Desktop-With-Nvidia


```
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg && curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list | sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
```

```
sed -i -e '/experimental/ s/^#//g' /etc/apt/sources.list.d/nvidia-container-toolkit.list
```

```
sudo apt-get update
```

```
sudo apt-get install -y nvidia-container-toolkit
```

```
sudo nvidia-ctk runtime configure --runtime=docker
```

## Run Docker to test Nvidia GPU

```
sudo docker run --rm --gpus all nvidia/cuda:12.8.1-cudnn-runtime-rockylinux8 nvidia-smi
```
```
sudo docker run --gpus all -d --name my-container nvidia/cuda:12.8.1-cudnn-runtime-rockylinux8 tail -f /dev/null
```

```
sudo docker exec -it my-container bash
```


```
dnf groupinstall "Development Tools"
```

```
dnf install python3.12
```

```
dnf install python3.12-pip -y
```

```
dnf install python3.12-devel
```

```
python3.12 -m pip install 'tensorflow[and-cuda]'
```


```
python3.12 -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"
```

