# Specify the minimum CMAKE version required
cmake_minimum_required(VERSION 3.1)
# Your project's name
project(Project3D)


set(SRC
    Application3D.cpp
    main.cpp
)

set(HEADERS
    Application3D.h
)

add_executable(${PROJECT_NAME} ${HEADERS} ${SRC})
target_link_libraries(${PROJECT_NAME} aieBootstrap)