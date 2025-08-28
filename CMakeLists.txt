cmake_minimum_required(VERSION 3.10)

project(LearnFFmpeg)

set(CMAKE_CXX_STANDARD 20)

set(FFMPEG_ROOT "/opt/homebrew/Cellar/ffmpeg/7.1.1_5") # 替换为你的FFmpeg安装路径

add_executable(${PROJECT_NAME} main.cpp)
target_include_directories(${PROJECT_NAME} PRIVATE ${FFMPEG_ROOT}/include)
target_link_directories(${PROJECT_NAME} PRIVATE ${FFMPEG_ROOT}/lib)

find_library(AVCODEC_LIBRARY avcodec)
find_library(AVFORMAT_LIBRARY avformat)
find_library(AVUTIL_LIBRARY avutil)
find_library(SWSCALE_LIBRARY swscale)
find_library(SWRESAMPLE_LIBRARY swresample)

find_package(Qt6 REQUIRED COMPONENTS Widgets)

target_link_libraries(${PROJECT_NAME} PRIVATE
        ${AVCODEC_LIBRARY}
        ${AVFORMAT_LIBRARY}
        ${AVUTIL_LIBRARY}
        ${SWSCALE_LIBRARY}
        ${SWRESAMPLE_LIBRARY}
        Qt6::Widgets
)

