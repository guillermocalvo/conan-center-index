cmake_minimum_required(VERSION 3.15)
project(test_package LANGUAGES CXX)

find_package(prometheus-cpp CONFIG REQUIRED)

add_executable(${PROJECT_NAME} test_package.cpp)
target_link_libraries(${PROJECT_NAME} PRIVATE prometheus-cpp::push prometheus-cpp::pull)
if(${prometheus-cpp_VERSION} VERSION_EQUAL "1.1.0")
    target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_14)
else()
    target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_11)
endif()
