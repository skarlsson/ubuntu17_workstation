# README #

```
sudo apt -y update
sudo apt-get install ssh ansible git aptitude

git config --global user.email "your@email"
git config --global user.name "your name"

git clone https://github.com/skarlsson/ubuntu18_workstation.git
cd ubuntu18_workstation
```

#### if you have a second ssd (YOUR SECOND SSD DEVICE IS LIKELY DIFFERENT!!!)
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

#### gui utils
```
ansible-playbook -i "localhost," -c local desktop.yml
```

#### tensorflow (without GPU)
```
ansible-playbook -i "localhost," -c local tensorflow.yml
```

#### clion
```
ansible-playbook -i "localhost," -c local jetbrains.yml
```
