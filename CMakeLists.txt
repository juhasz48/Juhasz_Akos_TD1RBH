cmake_minimum_required(VERSION 3.8)
project(grafika)

find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)


set(GLFW_INCLUDE_PATH "" CACHE PATH "C:/MinGW/include/GL" )
set(GLFW_LIBRARY "" CACHE FILEPATH "glfw.lib" )
set(GLEW_INCLUDE_PATH "" CACHE PATH "C:/MinGW/include/GL" )
set(GLEW_LIBRARY "" CACHE FILEPATH "glew.lib" )
set(SOIL_INCLUDE_PATH "" CACHE PATH "C:/MinGW/include/SOIL")
set(SOIL_INCLUDE_PATH "" CACHE PATH "soil.lib")

set(FREEGLUT_INCLUDE_DIRS freeglut/include)
set(FREEGLUT_LIBRARY_DIRS freeglut/lib)
set(FREEGLUT_LIBRARIES freeglut)


set(CMAKE_C_STANDARD 99)

set(HEADER_FILES
        camera.h
        draw.h
        model.h)
set(SOURCE_FILES
        camera.c
        draw.c
        main.c
        model.c
        )

include_directories(${GLFW_INCLUDE_PATH}
        $(GLEW_INCLUDE_PATH)
        $(SOIL_INCLUDE_PATH)
        $(FREEGLUT_INCLUDE_DIRS)

        )
link_directories( $(FREEGLUT_LIBRARY_DIRS))

add_executable(grafika ${SOURCE_FILES} ${HEADER_FILES})
target_link_libraries(grafika
        ${OPENGL_LIBRARY} # filled by "find_package(OpenGL REQUIRED)"
        ${GLFW_LIBRARY}
        ${GLEW_LIBRARY}
        ${SOIL_LIBRARY}
        ${FREEGLUT_LIBRARIES}
        )

