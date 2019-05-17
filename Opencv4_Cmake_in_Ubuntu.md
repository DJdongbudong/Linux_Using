# 方案一：
## reference: https://blog.csdn.net/zhangjunhit/article/details/85156760
## 资源
opencv.zip opencv_contrib.zip

## step 1: 官方指定依赖包：
```
sudo apt-get install build-essential
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
```

## step 2: 在opencv源代码文件夹 建立build文件夹 

## step 3：在build文件夹中，使用root权限打开 
```
cmake-gui ..
```

## step 4: cmake 设置 拓展程序和专利程序的路径安装+指定安装路径

## step 5： make install 进行安装库到 step 4 指定的本地文件夹

## step 6： 环境配置
```
#lib
/etc/ld.so.conf.d/opencv.conf
#pkg-config
/etc/bash.bashrc
```

# 方案二 ubuntu opencv 安装opencv
```
sudo apt-get install build-essential
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev

cd ~/opencv-3.4.3  # 进入opencv文件夹
mkdir build # 创建build文件夹
cd build # 进入build文件夹

#cmake指令，如果没有特殊要求建议就选择默认的就可以
#注意，后面的两个点千万不能省，代表了上级目录
cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local ..  
make -j7 # 多线程执行make任务

# 最后一步，安装库文件
sudo make install

# 更新库
sudo ldconfig
```

# 项目测试 cmake opencv
[reference](https://blog.csdn.net/github_30605157/article/details/79839177)
```
根目录：
	CMakeLists.txt
	src/main.cpp
步骤:
CMakeLists.txt
	# project name
	PROJECT(opencv_test)
	# requirement of cmake version
	cmake_minimum_required(VERSION 3.5)

	# set the directory of executable files
	set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${opencv_test_SOURCE_DIR}/bin)

	# find required opencv
	find_package(OpenCV REQUIRED)
	# directory of opencv headers
	include_directories(${OpenCV_INCLUDE_DIRS})
	# name of executable file and path of source file
	add_executable(opencv_test src/main.cpp)
	# directory of opencv library
	link_directories(${OpenCV_LIBRARY_DIRS})
	# opencv libraries
	target_link_libraries(opencv_test ${OpenCV_LIBS})
cd build
cmake ..
make
	
```
