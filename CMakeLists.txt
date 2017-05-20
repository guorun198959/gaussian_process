##########################################################################


cmake_minimum_required(VERSION 2.8.3)
project(gaussian_process)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
#  roscpp
)

## System dependencies are found with CMake's conventions
#find_package(Boost REQUIRED COMPONENTS thread)

###################################
## catkin specific configuration ##
###################################
## The catkin_package macro generates cmake config files for your package
## Declare things to be passed to dependent projects
## INCLUDE_DIRS: uncomment this if you package contains header files
## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need

catkin_package(
 INCLUDE_DIRS include
 LIBRARIES gaussian_process
 CATKIN_DEPENDS
#  roscpp
 DEPENDS
 Boost
)

###########
## Build ##
###########
include_directories(include ${Boost_INCLUDE_DIRS} ${catkin_INCLUDE_DIRS})


## Declare a cpp library                    
add_library(gaussian_process src/SingleGP.cpp src/covarianceFunctions.cpp)


## Specify libraries to link a library or executable target against
target_link_libraries(gaussian_process ${GSL_LIBRARIES})


#############
## Install ##
#############

# all install targets should use catkin DESTINATION variables
# See http://ros.org/doc/api/catkin/html/adv_user_guide/variables.html

## Mark executables and/or libraries for installation
install(TARGETS  gaussian_process
  #ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

## Install project namespaced headers
install(DIRECTORY include/gaussian_process/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
  #FILES_MATCHING PATTERN "*.h"
  PATTERN ".svn" EXCLUDE)
