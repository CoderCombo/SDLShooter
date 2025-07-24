# 标题
cmake_minimum_required(VERSION 3.10.0)
project(SDLShooter VERSION 0.1.0 LANGUAGES C CXX)

# 设置C++标准
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# 指定编译选项
add_compile_options(
    -Wall 
    -Wextra 
    -pedantic)

#include_directories("/usr/include/SDL2")
# 指定链接库目录 链接库哪里找？
#link_directories("/usr/lib/x86_64-linux-gnu")

# 设置编译输出目录
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_SOURCE_DIR})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_SOURCE_DIR})

set(TARGET ${PROJECT_NAME}_${CMAKE_SYSTEM_NAME})

# 查找SDL2库 并载入cmake预设
find_package(SDL2 REQUIRED)

#检查是否找到了所有组件
if(NOT TARGET SDL2::SDL2)
    message(FATAL_ERROR "SDL2 library not found!")
endif()

#add_executable(SDLShooter main.cpp)
add_executable(${TARGET} main.cpp)
# 链接那几个库
#target_link_libraries(SDLShooter SDL2::libSDL2main.a SDL2::libSDL2.a)
#target_link_libraries(${TARGET} 
#                      SDL2::SDL2main
#                        SDL2::SDL2
#                        ${SDL2_LIBRARIES}
#                        )
target_link_libraries(${TARGET} 
                        ${SDL2_LIBRARIES}
                        )