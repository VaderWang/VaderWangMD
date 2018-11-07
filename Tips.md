---
title: Tips
date: 2018-10-10 00:34:30
tags:
---

### VScode格式化代码

Windows:	Shift + Alt + F

Mac:		Shift + Option + F

Ubuntu:		 Ctrl + Shift + I

### IDEA格式化代码

快速抽取返回值：

control + alt + v

万能：

alt+enter 

点击showMenbers可以查看类中的方法等

格式化代码：

control + alt + shift + L

快速下一行：

win + shift + enter

提取变量：

control + alt + v

变量名大写：

control+ shift + u

批量修改变量名：

control + shift + alt + j

为了能够使用javac需要把下面路径加入环境变量Path

```
C:\Program Files\Java\jdk1.8.0_172\bin
```

### GIT冲突解决

方法一：stash

```
git stash
git pull
git stash pop
```

方法二：直接完全覆盖本地修改

```
git reset --hard
git pull
```

## Ubuntu

```shell
sudo gdebi xxx.deb
```

```shell
$ scp -r software/ vaderwang@ubuntu:/home/vaderwang/software
```

## Chrome

网页截图

开发者模式（F12）下control + shift + p 输入caputer full size screenshot即可

## VM

control + alt 弹出虚拟机

## CentOS

安装vscode

```shell
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
yum check-update
sudo yum install code
```

```shell
service network restart
```

## Logs

10:56	Error running 'RearServicesApplication': Command line is too long. Shorten command line for RearServicesApplication or also for Spring Boot default configuration.

Solve:

在该项目文件夹下.idea/workspace.xml中添加

```xml
<component name="PropertiesComponent">
  ...
  <property name="dynamic.classpath" value="true" />
</component>
```