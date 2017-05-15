# Specify the minimum CMAKE version required
cmake_minimum_required(VERSION 2.8)

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
SET(GLFW_BUILD_EXAMPLES NO)
SET(GLFW_BUILD_TESTS NO)

add_subdirectory(${CMAKE_SOURCE_DIR}/dependencies/glfw)


file(GLOB src in ${CMAKE_SOURCE_DIR}/bootstrap/*)


add_library(Bootstrap.lib ${src})
target_link_libraries(Bootstrap.lib glfw3)