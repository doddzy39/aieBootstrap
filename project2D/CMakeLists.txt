# Specify the minimum CMAKE version required
cmake_minimum_required(VERSION 3.1)
# Your project's name
project(Project2D)


set(SRC
    Application2D.cpp
    main.cpp
)

set(HEADERS
    Application2D.h
)

add_executable(${PROJECT_NAME} ${HEADERS} ${SRC})
target_link_libraries(${PROJECT_NAME} aieBootstrap)