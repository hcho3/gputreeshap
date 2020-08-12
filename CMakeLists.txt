cmake_minimum_required(VERSION 3.8 FATAL_ERROR)
project(GPUTreeShap LANGUAGES CXX CUDA)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CUDA_STANDARD 14)

find_package(GTest)
include_directories(${CMAKE_SOURCE_DIR})
add_executable(TestGPUTreeShap tests/test_gpu_treeshap.cu)
target_include_directories(TestGPUTreeShap  PRIVATE ${GTEST_INCLUDE_DIRS})
target_compile_options(TestGPUTreeShap PRIVATE $<$<COMPILE_LANGUAGE:CUDA>:-Xcompiler /WX>) 
target_link_libraries(TestGPUTreeShap  PRIVATE  ${GTEST_BOTH_LIBRARIES})