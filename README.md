# Armbian-Usage-Management
## 更新系统时间
```bash
timedatectl set-timezone "Asia/ShangHai" #设定+0800时区
timedatectl set-time "2022-02-28 19:12:40" #手动设定现在日期与时间
apt install -y ntp #安装ntp服务，自动校时
systemctl status ntp #查看ntp服务状态,显示active (running)代表已启用及执行中
```
## 修改国内源
### 修改sources.list
```bash
lsb_release -a #查看系统版本
nano /etc/apt/sources.list 
deb http://mirrors.ustc.edu.cn/debian buster main contrib non-free
deb http://mirrors.ustc.edu.cn/debian buster-updates main contrib non-free
deb http://mirrors.ustc.edu.cn/debian buster-backports main contrib non-free
deb http://mirrors.ustc.edu.cn/debian-security/ buster/updates main contrib non-free

deb http://mirrors.ustc.edu.cn/debian bullseye main contrib non-free
deb http://mirrors.ustc.edu.cn/debian bullseye-updates main contrib non-free
deb http://mirrors.ustc.edu.cn/debian bullseye-backports main contrib non-free
deb http://mirrors.ustc.edu.cn/debian-security/ bullseye/updates main contrib non-free


deb http://httpredir.debian.org/debian buster main contrib non-free
#deb-src http://httpredir.debian.org/debian buster main contrib non-free

deb http://httpredir.debian.org/debian buster-updates main contrib non-free
#deb-src http://httpredir.debian.org/debian buster-updates main contrib non-free

deb http://httpredir.debian.org/debian buster-backports main contrib non-free
#deb-src http://httpredir.debian.org/debian buster-backports main contrib non-free

deb http://security.debian.org/ buster/updates main contrib non-free
#deb-src http://security.debian.org/ buster/updates main contrib non-free
```
### 修改armbian.list
```
修改armbian.list
nano /etc/apt/sources.list.d/armbian.list
deb http://apt.armbian.com buster main buster-utils buster-desktop

deb https://mirrors.tuna.tsinghua.edu.cn/armbian bullseye main bullseye-utils bullseye-desktop

deb https://mirrors.ustc.edu.cn/armbian bullseye main bullseye-utils bullseye-desktop
```
### 更新系统软件索引
```bash
sudo apt-get update
apt update
apt upgrade
rm /var/lib/apt/lists/lock #更新如遇错误可以使用此命令
```
### 配置服务器DNS
```bash
nano /etc/resolv.conf
如果没有安装nano，则用:
vi /etc/resolv.conf

把nameserver后面的IP地址换成你的路由器地址，或者改成常用的几个DNS：

DNSPod（腾讯）DNS：
119.29.29.29
百度DNS：
180.76.76.76
阿里DNS：
223.5.5.5 / 223.6.6.6
114 DNS：
114.114.114.114
Google DNS：
8.8.8.8
修改完成，然后保存退出（nano:“Ctrl+X”; vim:先“Esc”然后“:wq”）即可。

这样基本可以解决不能解析主机的问题。
```

