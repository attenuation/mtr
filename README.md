## Linux安装方法(eg Debian,Ubuntu)
### 编译
  安装依赖:

        #Debian系列
        sudo apt-get update
        sudo apt-get install -y automake libncurses5-dev libncursesw5-dev
        #Archlinux
        sudo pacman -Syu
        sudo pacman -S base-devel ncurses
  如果需要biliip解析功能，请使用以下命令编译:

        ./bootstrap.sh
        ./configure --without-gtk --disable-ipv6 --with-biliip
        make -j8
        sudo make install

### 下载IP库  
  下载数据文件放置至/opt/mtr/BiliIP.dat

        sudo bash -c 'mkdir /opt/mtr && wget http://wsdownload.hdslb.net/BiliIP.dat.gz -O - | gzip -dc > /opt/mtr/BiliIP.dat'
	
  运行时使用以下两种方式：
  
        MTR_OPTIONS="-R" mtr
        mtr -R

## MAC 安装示例
 * 原生 mtr 添加了 位置显示 和 DNS反向解析。
### 编译环境准备

>    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

    brew install automake
    brew install wget
    brew install gtk+

### 下载源码

    git clone https://github.com/Bilibili/mtr

### 编译安装

    cd mtr
    ./bootstrap.sh 
    ./configure --without-gtk --disable-ipv6 --with-biliip 
    make -j8
    sudo bash -c 'cp mtr /usr/local/bin && mkdir /opt/mtr && chmod +s /usr/local/bin/mtr && mkdir -p /opt/mtr/BiliIP && wget http://wsdownload.hdslb.net/BiliIP.dat.gz -O - | gzip -dc > /opt/mtr/BiliIP.dat'

### Show一把
#### 原生

    sudo mtr www.bilibili.com

#### 扩展

    sudo mtr -R www.bilibili.com

#### 感谢

    IP库国家/城市数据来源：http://www.ipip.net/ 免费版
    IP库ISP来源：QQWry / 新浪公开IP查询库

#### 截图

![MAC运行截图](http://ww1.sinaimg.cn/large/64bb76b9gw1ev01oyul45j20pd0b441o.jpg)
