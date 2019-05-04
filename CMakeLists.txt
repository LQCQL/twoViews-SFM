cmake_minimum_required(VERSION 2.8)
project(twoViewsSFM)

set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake/" ${CMAKE_MODULE_PATH})

# Eigen (required)
find_package(Eigen REQUIRED)
include_directories(${EIGEN_INCLUDE_DIRS})
add_definitions(-DEIGEN_USE_NEW_STDVECTOR -DEIGEN_YES_I_KNOW_SPARSE_MODULE_IS_NOT_STABLE_YET)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "-fPIC")

add_subdirectory(core)
add_subdirectory(util)
add_subdirectory(features)
add_subdirectory(sfm)

#test bundle adjustment
add_executable(twoViewsSFM main.cpp)
target_link_libraries(twoViewsSFM sfm util core features)
