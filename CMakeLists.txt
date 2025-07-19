cmake_minimum_required(VERSION 3.10.0)
project(SDLShooter VERSION 0.1.0 LANGUAGES C CXX)

# 预处理阶段 指定包含头文件路径
include_directories("/usr/include/SDL2")
# 指定链接库目录 链接库哪里找？
link_directories("/usr/lib/x86_64-linux-gnu")

add_executable(SDLShooter main.cpp)
# 链接那几个库
target_link_libraries(SDLShooter libSDL2main.a libSDL2.a)