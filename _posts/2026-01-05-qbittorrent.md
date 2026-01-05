---
layout: blog-post
title: "qbittorrent"
date: 2026-01-05 
---
## 一、对于Debian的发行版，可以直接使用以下命令安装qbittorrent-nox：
sudo apt install qbittorrent-nox -y
## 二、设置开机自启动：
修改（如有）或创建/etc/systemd/system/qbittorrent-nox.service文件：
nano /etc/systemd/system/qbittorrent-nox.service
## 把以下内容复制进去：
[Unit]
Description=qBittorrent-nox
After=network.target
[Service]
User=root
Type=forking
RemainAfterExit=yes
ExecStart=/usr/bin/qbittorrent-nox -d
[Install]
WantedBy=multi-user.target
## 按Ctrl+O保存，再按确定键确定然后Ctrl+x退出。
## 修改qbittorrent-nox.service文件后重新载入：
sudo systemctl daemon-reload
## 设置开机启动：
sudo systemctl enable qbittorrent-nox
## 启动qbittorrent-nox：
sudo systemctl start qbittorrent-nox
## 停止qbittorrent-nox：
sudo systemctl stop qbittorrent-nox
安装好后，打开浏览器，输入http://ip地址:8080，就可以打开qbittorrent-nox的webui了，用默认的用户名admin，默认密码adminadmin可以登陆，进去后设置语言为中文，设置下载路径，就可以使用了。

#注意：
如果安装时提示无法定位（或者找不到）qbittorrent-nox，可以添加qbittorrent-nox的PPA软件源。
例如在ubuntu中可以按照如下方式添加：
#安装add-apt-repository
apt install software-properties-common -y
#添加qbittorrent-nox的PPA软件源
# qBittorrent 稳定版
sudo add-apt-repository ppa:qbittorrent-team/qbittorrent-stable
# qBittorrent 测试版
sudo add-apt-repository ppa:qbittorrent-team/qbittorrent-unstable
apt update && apt upgrade -y
添加完成后就可以安装qbittorrent-nox了。
