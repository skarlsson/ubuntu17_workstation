# README #

```
sudo apt -y update
sudo apt-get install ssh ansible git aptitude wget unzip
wget https://github.com/skarlsson/ubuntu18_workstation/archive/master.zip
unzip master.zip
cd ubuntu18_workstation-master
```

##### OPTIONAL if you have a second ssd/harddrive (YOUR DEVICENAME IS LIKELY DIFFERENT!!!)
```
lsblk

sudo parted /dev/nvme1n1 mklabel gpt
sudo parted /dev/nvme1n1 -a optimal mkpart primary ext4 0% 100%
time for a reboot...

ansible-playbook -i "localhost," -c local --extra-vars "second_ssd_device=/dev/nvme1n1p1" mount_second_ssd_device.yml --ask-sudo-pass 
```

```
ansible-playbook -i "localhost," -c local initial-ubuntu18.yml --ask-sudo-pass 
```

###### if you nned cuda a reboot is nessesary to load the new driver
```
nvidia-smi 
Fri Dec 25 16:49:12 2015
+------------------------------------------------------+
| NVIDIA-SMI 352.63     Driver Version: 352.63         |
|-------------------------------+----------------------+
```


