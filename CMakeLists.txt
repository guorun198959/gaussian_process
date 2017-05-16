cmake_minimum_required(VERSION 2.8.3)
project(gaussian_process)

find_package(catkin REQUIRED)

catkin_package()

include_directories(include ${catkin_INCLUDE_DIRS})

add_library(gaussian_process src/SingleGP.cpp src/covarianceFunctions.cpp)

target_link_libraries(gaussian_process ${GSL_LIBRARIES})
