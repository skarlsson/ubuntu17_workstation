# README #

```
sudo apt-get install ssh ansible git

git config --global user.email "svante.karlsson@csi.se"
git config --global user.name "svante karlsson"


copy your ssh keys .to .ssh
chmod 400 ~/.ssh/id_rsa
chmod 700 ~/.ssh
mkdir ansible 
cd ansible
git clone git@bitbucket.org:bitbouncer/ansible_ubuntu_desktop.git
```

#if you have a second ssd
```
lsblk

sudo parted /dev/nvme1n1 mklabel gpt
sudo parted /dev/nvme1n1 -a optimal mkpart primary ext4 0% 100%
time for a reboot...

ansible-playbook -i "localhost," -c local --extra-vars "second_ssd_device=/dev/nvme1n1p1" mount_second_ssd_device.yml --ask-sudo-pass 
```


ansible-playbook -i "localhost," -c local common.yml --ask-sudo-pass 

ansible-playbook -i "localhost," -c local kafka.yml

ansible-playbook -i "localhost," -c local monitoring.yml

ansible-playbook -i "localhost," -c local tensorflow.yml