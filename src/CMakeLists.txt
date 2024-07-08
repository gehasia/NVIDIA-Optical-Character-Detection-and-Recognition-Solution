cmake_minimum_required(VERSION 3.14)

project(NVIDIA-OCR_Lib LANGUAGES CXX CUDA)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(libsrc nvOCDR.cpp)

add_library(NVIDIA-OCR_Lib OBJECT ${libsrc})

target_include_directories(NVIDIA-OCR_Lib PRIVATE ../include)
target_sources(NVIDIA-OCR_Lib PUBLIC
  kernel.cu
  ../include/nvocdr.h
  kernel.h MemManager.h nvOCDR.h OCDNetEngine.h OCRNetEngine.h RectEngine.h TRTEngine.h utils.h
  MemManager.cpp nvOCDR.cpp OCDNetEngine.cpp OCRNetEngine.cpp RectEngine.cpp TRTEngine.cpp
  CMakeLists.txt
)


#set_property(TARGET NVIDIA-OCR_Lib PROPERTY POSITION_INDEPENDENT_CODE 1)
#add_library(NVIDIA-OCR_Lib_shared SHARED $<TARGET_OBJECTS:NVIDIA-OCR_Lib>)

add_library(NVIDIA-OCR_Lib_static STATIC $<TARGET_OBJECTS:NVIDIA-OCR_Lib>)

add_library(cublas SHARED IMPORTED )
add_library(cudart SHARED IMPORTED )
add_library(opencv_core SHARED IMPORTED )
add_library(opencv_imgproc SHARED IMPORTED )
add_library(opencv_imgcodecs SHARED IMPORTED )

set_target_properties(cublas PROPERTIES IMPORTED_LOCATION /opt/cuda/targets/x86_64-linux/lib/libcublas.so)
set_target_properties(cudart PROPERTIES IMPORTED_LOCATION /opt/cuda/targets/x86_64-linux/lib/libcudart.so)
set_target_properties(opencv_core PROPERTIES IMPORTED_LOCATION /usr/lib/libopencv_core.so)
set_target_properties(opencv_imgproc PROPERTIES IMPORTED_LOCATION /usr/lib/libopencv_imgproc.so)
set_target_properties(opencv_imgcodecs PROPERTIES IMPORTED_LOCATION /usr/lib/libopencv_imgcodecs.so)



target_link_libraries(NVIDIA-OCR_Lib_static
   nvinfer
   cudart
   opencv_core
   opencv_imgproc
   opencv_imgcodecs
   cublas
   nvinfer_plugin
)

target_include_directories(NVIDIA-OCR_Lib  PUBLIC
    /usr/include/opencv4
    /opt/cuda/include
)

target_compile_definitions(NVIDIA-OCR_Lib  PRIVATE NVIDIAOPTICALCHARACTERDETECTIONANDRECOGNITIONSOLUTION_LIBRARY)


