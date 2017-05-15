# Specify the minimum CMAKE version required
cmake_minimum_required(VERSION 3.1)

set(CMAKE_CXX_STANDARD 11)

# Your project's name
project(aieBootstrap)

# Header only dependencies
include_directories(${CMAKE_SOURCE_DIR}/dependencies/glm)
include_directories(${CMAKE_SOURCE_DIR}/dependencies/imgui)
include_directories(${CMAKE_SOURCE_DIR}/dependencies/stb)
include_directories(${CMAKE_SOURCE_DIR}/dependencies/glfw/include)
include_directories(${CMAKE_SOURCE_DIR}/dependencies/libsndfile/include)
include_directories(${CMAKE_SOURCE_DIR}/dependencies/openal/include)

#Cmake supporting dependencies
option(GLFW_BUILD_EXAMPLES NO)
option(GLFW_BUILD_TESTS NO)


add_subdirectory(${CMAKE_SOURCE_DIR}/dependencies/glfw)


file(GLOB src in ${CMAKE_SOURCE_DIR}/bootstrap/*)


add_library(Bootstrap ${src})
target_link_libraries(Bootstrap glfw3)