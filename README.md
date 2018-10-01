# Setup-Machine

#Update UBUNTU
sudo apt-get update
sudo apt-get --assume-yes upgrade
sudo apt-get --assume-yes install tmux build-essential gcc g++ make binutils
sudo apt-get --assume-yes install software-properties-common
sudo apt-get --assume-yes install git

#Verify pre-requisites for CUDA
sudo apt install gcc
gcc --version

#Download CUDA install from NVIDIA website and select the version corresponding to your distribution
https://developer.nvidia.com/cuda-downloads

sudo dpkg -i cuda-repo-ubuntu1804-10-0-local-10.0.130-410.48_1.0-1_amd64.deb
sudo apt-key add /var/cuda-repo-10-0-local-10.0.130-410.48/7fa2af80.pub
sudo apt-get update
sudo apt-get install cuda

#After installation, add CUDA folder to PATH
cat >> ~/.bashrc << 'EOF'
export PATH=/usr/local/cuda-10.0/bin${PATH:+:${PATH}}
EOF
source ~/.bashrc



Install NVIDIA drivers

https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa


Check if:
PATH includes /usr/local/cuda-10.0/bin
LD_LIBRARY_PATH includes /usr/local/cuda-10.0/lib64, or, add /usr/local/cuda-10.0/lib64 to /etc/ld.so.conf and run ldconfig as root
 if not add this to .profile in home directory
 
#Install RStudio server (for 64 bit)
sudo apt-get --assume-yes update
sudo apt-get --assume-yes install r-base
sudo apt-get install gdebi-core
wget https://download2.rstudio.org/rstudio-server-1.1.456-amd64.deb
sudo gdebi rstudio-server-1.1.456-amd64.deb

#Setting up Jupyter
##Create a ~/.jupyter/jupyter_notebook_config.py with settings
jupyter notebook --generate-config
jupyter notebook --port=8888 --NotebookApp.token='' # Start it

##Replace 'path-to-jupyter' with the actual path to the jupyter
##installation (run 'which jupyter' if you don't know it). Also
##'path-to-dir' should be the dir where your deep learning notebooks 
##would reside (I use ~/DL/)
@reboot path-to-jupyter notebook --no-browser --port=8888 --NotebookApp.token='' --notebook-dir path-to-dir &

