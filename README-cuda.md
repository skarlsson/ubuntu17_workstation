Make sure you have installed the NVIDIA driver and Docker 19.03 for your Linux distribution

nvidia cuda vs driver
10.1	>= 418.39	>= 3.0 (Kepler)

docker --version

nvidia-smi 
Fri Dec 25 16:49:12 2015
+------------------------------------------------------+
| NVIDIA-SMI 352.63     Driver Version: 352.63         |
|-------------------------------+----------------------+

#how to purge
sudo apt-get purge nvidia*
#reboot

#install a new one
3sudo apt search nvidia-driver
sudo apt-get install nvidia-driver-435

#make sure you have a late enough driver
nvidia-smi

##now you can add cuda
ansible-playbook -i "localhost," -c local initial-cuda.yml --ask-sudo-pass 

#reboot or restart docker
and test that it works


docker run --gpus all nvidia/cuda:9.0-base nvidia-smi


