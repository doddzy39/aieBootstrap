# Specify the minimum CMAKE version required
cmake_minimum_required(VERSION 3.1)

set(CMAKE_CXX_STANDARD 11)

# Your project's name
project(aieBootstrap)

find_package(OpenGL REQUIRED)

# Header only dependencies
include_directories(${PROJECT_SOURCE_DIR}/dependencies/glm)
include_directories(${PROJECT_SOURCE_DIR}/dependencies/imgui)
include_directories(${PROJECT_SOURCE_DIR}/dependencies/stb)
include_directories(${PROJECT_SOURCE_DIR}/dependencies/glfw/include)
include_directories(${PROJECT_SOURCE_DIR}/dependencies/libsndfile/include)
include_directories(${PROJECT_SOURCE_DIR}/dependencies/openal/include)

SET(GLM_INCLUDE_PATH ${PROJECT_SOURCE_DIR}/dependencies/glm CACHE PATH "GLM Include Path")

#Cmake supporting dependencies
option(GLFW_BUILD_EXAMPLES NO)
option(GLFW_BUILD_TESTS NO)


add_subdirectory(${PROJECT_SOURCE_DIR}/dependencies/glfw)


file(GLOB src in ${PROJECT_SOURCE_DIR}/bootstrap/*)

set( IMGUI_SRC
   dependencies/imgui/imgui.cpp 
   dependencies/imgui/imgui_draw.cpp
)

add_library(Bootstrap ${src} ${IMGUI_SRC})
target_link_libraries(Bootstrap glfw)

target_include_directories(Bootstrap PUBLIC
    ${PROJECT_SOURCE_DIR}/bootstrap
)

 target_link_libraries(Bootstrap ${OPENGL_gl_LIBRARY})