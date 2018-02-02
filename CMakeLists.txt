# Specify the minimum CMAKE version required
cmake_minimum_required(VERSION 3.2)
set(CMAKE_CXX_STANDARD 14)

# Your project's name
project(aieBootstrap)

find_package(OpenGL REQUIRED)

# Header only dependencies
include_directories(${PROJECT_SOURCE_DIR}/dependencies/glm)
include_directories(${PROJECT_SOURCE_DIR}/dependencies/imgui)
include_directories(${PROJECT_SOURCE_DIR}/dependencies/stb)
include_directories(${PROJECT_SOURCE_DIR}/dependencies/glfw/include)
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

add_library(aieBootstrap ${src} ${IMGUI_SRC})
target_link_libraries(aieBootstrap glfw)

target_include_directories(aieBootstrap PUBLIC
    ${PROJECT_SOURCE_DIR}/bootstrap
)

 target_link_libraries(aieBootstrap ${OPENGL_gl_LIBRARY})

 #Update the line below to select which project to build
 add_subdirectory(project3D)