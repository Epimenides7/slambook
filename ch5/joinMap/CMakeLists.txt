cmake_minimum_required( VERSION 2.8 )
project( joinMap )

set( CMAKE_BUILD_TYPE Release )
set( CMAKE_CXX_FLAGS "-std=c++11 -O3" )

# opencv 
find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_INCLUDE_DIRS} )

# eigen 
# include_directories( "/usr/include/eigen3/" )

# in osx and brew install
include_directories( /usr/local/Cellar/eigen/3.3.7/include/eigen3 )


# pcl 
# 用了component参数
find_package( PCL REQUIRED COMPONENT common io )
include_directories( ${PCL_INCLUDE_DIRS} )
# 添加编译参数
add_definitions( ${PCL_DEFINITIONS} )

add_executable( joinMap joinMap.cpp )
target_link_libraries( joinMap ${OpenCV_LIBS} ${PCL_LIBRARIES} )
