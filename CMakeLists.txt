cmake_minimum_required(VERSION 3.15)
project(second_homwork)

set(CMAKE_CXX_STANDARD 14)

set(CMAKE_BUILD_TYPE Debug )
add_definitions("-DENABLE_SSE")
set(CMAKE_CXX_FLAGS "-std=c++11 ${SSE_FLAGS}  ")
#-march=native

find_package(OpenCV 4 REQUIRED)
find_package(Sophus REQUIRED)
find_package(Sophus REQUIRED)
find_package(Pangolin REQUIRED)
include_directories(${Sophus_INCLUDE_DIRS})

include_directories(
        ${OpenCV_INCLUDE_DIRS}
        "/usr/include/eigen3/"
        ${Sophus_INCLUDE_DIRS}
        ${Pangolin_INCLUDE_DIRS}
)

add_subdirectory(./src)
aux_source_directory(./src SRC)

SET(G2O_LIBS g2o_csparse_extension g2o_stuff g2o_core cxsparse)
add_executable(FITBALL main.cpp ${SRC})
target_link_libraries(FITBALL ${OpenCV_LIBS} ${EIGEN_LIBS} ${OpenCV_LIBS} ${Pangolin_LIBRARIES} ${Sophus_LIBRARIES} ${G2O_LIBS})