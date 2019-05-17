# reference: https://blog.csdn.net/zhangjunhit/article/details/85156760
# 资源
opencv.zip opencv_contrib.zip

# step 1: 官方指定依赖包：
```
sudo apt-get install build-essential
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
```

# step 2: 在opencv源代码文件夹 建立build文件夹 

# step 3：在build文件夹中，使用root权限打开 
```
cmake-gui ..
```

# step 4: cmake 设置 拓展程序和专利程序的路径安装+指定安装路径

# step 5： make install 进行安装库到 step 4 指定的本地文件夹

# step 6： 环境配置
```
#lib
/etc/ld.so.conf.d/opencv.conf
#pkg-config
/etc/bash.bashrc
```
