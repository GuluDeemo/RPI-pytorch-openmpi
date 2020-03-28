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

python3 -m pip install Pillow==6.1, torchvision, graphviz

```