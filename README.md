# RPI-pytorch-openmpi

```
sudo apt update

sudo apt install libopenblas-dev graphviz -y

# install openmpi3

sudo apt install openmpi-bin openmpi-common openssh-client openssh-server libopenmpi3 libopenmpi-dev -y

# fix the bug "ModuleNotFoundError: No module named torch._C"

cd /home/pi/.local/lib/python3.7/site-packages/torch
sudo cp _C.cpython-37m-arm-linux-gnueabi.so _C.so
sudo cp _dl.cpython-37m-arm-linux-gnueabi.so _dl.so
cd ~

# install packages

python3 -m pip install Pillow==6.1
python3 -m pip install torchvision
python3 -m pip install graphviz

```
# Set up hostfile

```
sudo nano /etc/hosts
sudo nano /etc/hostname
```

# Set up NFS

## Set up NFS server

```
sudo apt update
sudo apt install nfs-kernel-server nfs-common -y
cd ~
mkdir MpiShare
sudo echo "/home/meng/MpiShare *(rw,sync,no_root_squash,no_subtree_check)" >> /etc/exports
sudo /etc/init.d/rpcbind restart
sudo /etc/init.d/nfs-kernel-server restart
```

## Set up NFS client

```
sudo apt install nfs-common -y
showmount -e node0
cd ~
mkdir MpiShare
sudo echo "node0:/home/meng/MpiShare /home/pi/MpiShare nfs defaults 0 0" >> /etc/fstab
sudo mount -a
```