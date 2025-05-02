# Relion Install





This repository provides the implementation of [Relion 5.0](https://relion.readthedocs.io/en/release-5.0/Installation.html):


这里详细记录了relion5.0部署在windows本地的详细过程

## windows 10/11 安装Linux子系统

relion本身依赖于Linux系统，因此需要在windows下安装一个子系统。详情参考[link](https://gitcode.csdn.net/66c55fe90bfad230b8ae218a.html?dp_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6Mzc2MDIyNywiZXhwIjoxNzQ2NDM4MjMyLCJpYXQiOjE3NDU4MzM0MzIsInVzZXJuYW1lIjoicXFfNDA3NzYxNzkifQ.AmEtK6OoVDGfr-L0XohmRWjoH59YMi3D71K-kvuilc8&spm=1001.2101.3001.6650.7&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7Eactivity-7-139008248-blog-137632509.235%5Ev43%5Econtrol&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7Eactivity-7-139008248-blog-137632509.235%5Ev43%5Econtrol&utm_relevant_index=13)


## 过WSL2安装图形化界面

由于relion可以进行图形化界面操作，因此需要再WSL上安装图形化界面。详细参考[link](https://blog.csdn.net/fysuccess/article/details/141646840?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EYuanLiJiHua%7ECtr-2-141646840-blog-140029025.235%5Ev43%5Epc_blog_bottom_relevance_base7&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EYuanLiJiHua%7ECtr-2-141646840-blog-140029025.235%5Ev43%5Epc_blog_bottom_relevance_base7)

最重要的代码如下：

```
sudo apt update
sudo apt upgrade -y
sudo apt install build-esstential

# 安装xfce4
sudo apt install xfce4

# 再bashrc最后一行添加如下内容并保存,把其中的172.30.16.1换成自己wsl的ipv4地址即可
sudo vim  ~/.bashrc 
export DISPLAY=172.30.16.1:0

source ~/.bashrc

#重启一下wsl子系统，具体方法是，在windows终端里运行以下指令，再重新打开
wsl --shutdown

#使用sudo 启动 Xfce 会话：
sudo startxfce4

```

## relion 的安装


关键步骤 [link](https://blog.csdn.net/yy19980310/article/details/119956571)

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