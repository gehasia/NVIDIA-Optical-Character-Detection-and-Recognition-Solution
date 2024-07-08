cmake_minimum_required(VERSION 3.14)

project(NVIDIA-Optical-Character-Detection-and-Recognition-Solution LANGUAGES CXX CUDA)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(src)
add_subdirectory(c++_samples/crop_based_inference)
add_subdirectory(c++_samples/crop_based_inference_vit)
add_subdirectory(c++_samples/simple_inference)
add_subdirectory(c++_samples/simple_inference_vit)



