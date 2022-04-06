# [python3 源码安装](https://github.com/stormzhai/gitblog/issues/7)

# 1 安装
sudo yum -y groupinstall “Development tools” 
sudo yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel python3-devel 
sudo wget https://www.python.org/ftp/python/3.6.2/Python-3.6.2.tar.xz 
sudo mkdir /usr/local/python3 
tar -xvJf Python-3.6.2.tar.xz 
cd Python-3.6.2 
./configure –prefix=/usr/local/python3
 sudo make && sudo make install
添加环境变量:
sudo vi /etc/profile
将下面内容添加到文件的最下面
PATH=$PATH:/usr/local/python3/bin
随后使环境变量生效
source /etc/profile

# 2 配置

2.1配置pip国内源：sudo cp pip.conf /etc/pip.conf
2.2安装Python虚拟环境：sudo pip3 install virtualenv
2.3创建Python虚拟环境：virtualenv -p python3 venv
2.4激活Python虚拟环境：source venv/bin/activate
2.5安装pip包：pip3 install -r requirements.txt -r requirements_dev.txt
2.6 退出虚拟环境，安装完成：deactivate