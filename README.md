# README #

```
sudo apt -y update
sudo apt-get install ssh ansible git aptitude

git config --global user.email "your@email"
git config --global user.name "your name"

git clone https://github.com/skarlsson/ubuntu18_workstation.git
cd ubuntu18_workstation
```

##### OPTIONAL if you have a second ssd/harddrive (YOUR DEVICENAME IS LIKELY DIFFERENT!!!)
```
lsblk

sudo parted /dev/nvme1n1 mklabel gpt
sudo parted /dev/nvme1n1 -a optimal mkpart primary ext4 0% 100%
time for a reboot...

ansible-playbook -i "localhost," -c local --extra-vars "second_ssd_device=/dev/nvme1n1p1" mount_second_ssd_device.yml --ask-sudo-pass 
```

#### basic non gui stuff
```
ansible-playbook -i "localhost," -c local initial-ubuntu18.yml --ask-sudo-pass 
```

#####run his to be able to run docker without sudo
```
sudo usermod -aG docker $USER
```

##### OPTIONAL how to install cuda

`latest cuda vs driver
10.1	>= 418.39
`
###### check what you have
```
nvidia-smi 
Fri Dec 25 16:49:12 2015
+------------------------------------------------------+
| NVIDIA-SMI 352.63     Driver Version: 352.63         |
|-------------------------------+----------------------+
```

###### if you need to purge driver
```
sudo apt-get purge nvidia*
reboot (?)
sudo apt-get install nvidia-driver-435
```

###### install latest cuda (10.1)
```
ansible-playbook -i "localhost," -c local initial-cuda.yml --ask-sudo-pass 
docker run --gpus all nvidia/cuda:9.0-base nvidia-smi
```

###### install older cuda (10.0)
```
ansible-playbook -i "localhost," -c local initial-cuda10.0.yml --ask-sudo-pass 
docker run --gpus all nvidia/cuda:9.0-base nvidia-smi
```
