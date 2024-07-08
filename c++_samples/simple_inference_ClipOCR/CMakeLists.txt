cmake_minimum_required(VERSION 3.14)

project(NVIDIA-OCR_Samples_simple_inference_ClipOCR LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(NVIDIA-OCR_Samples_simple_inference_ClipOCR simple_inference_ClipOCR.cpp)
target_link_libraries(NVIDIA-OCR_Samples_simple_inference_ClipOCR NVIDIA-Optical-Character-Detection-and-Recognition-Solution)
