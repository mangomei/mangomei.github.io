# 新电脑的经验积累
> 总结新电脑，安装了新的系统后，如何快速构建个人需要的用户环境。

以下为windows的相关经验。
## 装机篇
包含如下常用装机软件：
* 腾讯电脑管家
* 驱动安装，可使用驱动精灵，或者主板对于的管家，比如ASUS管家等，还可以用windows自带的设备管理器右键有问题的设备在网络中找适合的驱动。
* Google浏览器(可在软件管家中安装)
* [GHelper](https://d3.itmopcdn.com/down8/ghelper_v2.6.2_itmop.com.zip) - 安装VPN
* 搜狗拼音(可在软件管家中安装)
* 微信(可在软件管家中安装)



## 编程篇
### 安装git
1. 先下载 [git](https://git-scm.com/download/win)
2. 生成ssh key
``` shell
git config --global user.email "1092017732@qq.com"
git config --global user.name "mangodiy"
ssh-keygen -t rsa -b 4096 -C "1092017732@qq.com"
```
3. 到对应用户的`.ssh`目录下，查看公钥，并配置到在线仓库
``` shell
cat ~/.ssh/id_rsa.pub
```

### 安装jdk
1. 先下载 [jdk17](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)
2. 安装后，设置环境变量。
``` shell
C:\Users\mangodiy>java -version
java version "17.0.11" 2024-04-16 LTS
Java(TM) SE Runtime Environment (build 17.0.11+7-LTS-207)
Java HotSpot(TM) 64-Bit Server VM (build 17.0.11+7-LTS-207, mixed mode, sharing)
```

### 常用工具
1. [vscode](https://code.visualstudio.com/)
2. [idea](https://www.jetbrains.com/idea/download/?section=windows)