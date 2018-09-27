# Setup-Machine

Install NVIDIA drivers

https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa

Install CUDA

https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=runfilelocal
Run `sudo sh cuda_10.0.130_410.48_linux.run`

Check if:
PATH includes /usr/local/cuda-10.0/bin
LD_LIBRARY_PATH includes /usr/local/cuda-10.0/lib64, or, add /usr/local/cuda-10.0/lib64 to /etc/ld.so.conf and run ldconfig as root
 if not add this to .profile in home directory
