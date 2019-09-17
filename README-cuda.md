Make sure you have installed the NVIDIA driver and Docker 19.03 for your Linux distribution

docker --version
>=19.03

nvidia cuda vs driver
10.1	>= 418.39	>= 3.0 (Kepler)

>nvidia-smi 
Fri Dec 25 16:49:12 2015
+------------------------------------------------------+
| NVIDIA-SMI 352.63     Driver Version: 352.63         |
|-------------------------------+----------------------+


sudo apt-get purge nvidia*


sudo apt search nvidia-driver
sudo apt-get install nvidia-driver-435

>nvidia-smi
make sure you have a late enough driver



ansible-playbook -i "localhost," -c local initial-cuda.yml --ask-sudo-pass 


# Running an interactive CUDA session isolating the first GPU
docker run -ti --rm --runtime=nvidia -e NVIDIA_VISIBLE_DEVICES=0 nvidia/cuda





# Add the package repositories
$ distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
$ curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
$ curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list

$ sudo apt-get update && sudo apt-get install -y nvidia-container-toolkit
$ sudo systemctl restart docker
