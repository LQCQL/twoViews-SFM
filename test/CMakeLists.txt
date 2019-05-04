project(testsfm)
set(CMAKE_CXX_FLAGS  "-fPIC")
set(CMAKE_CXX_STANDARD  11)

include_directories("..")

add_executable(test main.cpp)
target_link_libraries(test sfm util core features)
