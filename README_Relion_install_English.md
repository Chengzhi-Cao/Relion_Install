# Relion Install





This repository provides the implementation of [Relion 5.0](https://relion.readthedocs.io/en/release-5.0/Installation.html):



## windows 10/11 Install Linux subsystem

RELION itself depends on the Linux system, so a subsystem needs to be installed on Windows. For details, refer to[link](https://gitcode.csdn.net/66c55fe90bfad230b8ae218a.html?dp_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6Mzc2MDIyNywiZXhwIjoxNzQ2NDM4MjMyLCJpYXQiOjE3NDU4MzM0MzIsInVzZXJuYW1lIjoicXFfNDA3NzYxNzkifQ.AmEtK6OoVDGfr-L0XohmRWjoH59YMi3D71K-kvuilc8&spm=1001.2101.3001.6650.7&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7Eactivity-7-139008248-blog-137632509.235%5Ev43%5Econtrol&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7Eactivity-7-139008248-blog-137632509.235%5Ev43%5Econtrol&utm_relevant_index=13)


## Install GUI on WSL2

Since Relion supports GUI, it must be installed on WSL. Please refer to [link](https://blog.csdn.net/fysuccess/article/details/141646840?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EYuanLiJiHua%7ECtr-2-141646840-blog-140029025.235%5Ev43%5Epc_blog_bottom_relevance_base7&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EYuanLiJiHua%7ECtr-2-141646840-blog-140029025.235%5Ev43%5Epc_blog_bottom_relevance_base7)


**Code：**

```
sudo apt update
sudo apt upgrade -y
sudo apt install build-esstential

# Install xfce4
sudo apt install xfce4

# Add the following line at the end of your .bashrc file and save it. Replace 172.30.16.1 with your WSL's IPv4 address.

sudo vim  ~/.bashrc 
export DISPLAY=172.30.16.1:0

source ~/.bashrc

#Restart the WSL subsystem by running the following command in Windows Terminal, then reopen it

wsl --shutdown

#Launch the Xfce session using sudo

sudo startxfce4

```

## Install relion


Key steps: [link](https://blog.csdn.net/yy19980310/article/details/119956571)

```
git clone https://github.com/3dem/relion.git


cd relion
git checkout master
mkdir build
cd build


cmake ..


make -j 4


# 但是在安装完成后可能无法直接使用，提示：
relion: command not found

# 这是因为官方在github教程中没有加设置环境变量的步骤，过程如下：
vim ~/.bashrc

# 在底部添加一行语句：
export PATH="/your/path/to/relion/build/bin:$PATH"

# 使生效：
source  ~/.bashrc


```