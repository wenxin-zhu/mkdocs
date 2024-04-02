![image-20230413011019341](https://zwx-pic.oss-cn-beijing.aliyuncs.com/img/image-20230413011019341.png)

> 编写项目代码的步骤

1、新建一个文件夹，用于存放你的项目文件，并且用vscode打开它。

2、新建一个include文件夹，用于存放所有的头文件，注意头文件的编写注意点。

3、新建一个src文件夹，用于存放所有的源文件。

4、根目录下放一个main.cc，用来编写main函数。

5、写好cmake lists文件，存放在根目录。

6、执行以下命令，进行编译

```shell
# 新建一个build文件夹，用于存放cmake编译信息，不用自己管
mkdir build 
# 进入build文件夹
cd build    
# 调用cmake工具，“..”表示cmake lists文件所在的路径。
cmake ..     
# 执行编译链接，得到可执行文件，会自动存放在build文件夹中
make          
# 运行可执行文件（程序）
./tjurm_tutorial 

```

> exec.cmd

```shell
@echo off

if exist build (
    echo build exist
) else (
    mkdir build
)
cd build
cmake -G "MinGW Makefiles" ..
mingw32-make
exe_cmake
```

> CMakeLists.txt

```cmake
cmake_minimum_required(VERSION 3.5) 
# 项目名称
project(exe_cmake)  

# 设置编译器
set(CMAKE_C_COMPILER "gcc")
set(CMAKE_CXX_COMPILER "g++")

# c++版本为c++11，
set(CMAKE_CXX_STANDARD 11)
# 编译类型:Debug(调试), Release(发布)
set(CMAKE_BUILD_TYPE RELEASE)                               
# C++编译选项(优化程度为-O3)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -w -O3 -g")         

# 头文件所在的目录
include_directories(${CMAKE_SOURCE_DIR}/include)

# 所有的源文件路径
file(GLOB_RECURSE sources ${CMAKE_SOURCE_DIR}/src/*.cpp)

# 可执行文件包含的源文件
add_executable(exe_cmake main.cc ${sources})
```

