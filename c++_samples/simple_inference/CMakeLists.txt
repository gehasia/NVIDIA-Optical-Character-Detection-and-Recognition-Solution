cmake_minimum_required(VERSION 3.14)

project(NVIDIA-OCR_Samples_simple_inference LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(NVIDIA-OCR_Samples_simple_inference simple_inference.cpp)
target_link_libraries(NVIDIA-OCR_Samples_simple_inference NVIDIA-OCR_Lib_static)

target_include_directories(NVIDIA-OCR_Samples_simple_inference   PUBLIC
    /usr/include/opencv4
    /opt/cuda/include
)
