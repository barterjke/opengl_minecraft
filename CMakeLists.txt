cmake_minimum_required(VERSION 3.0)
project(main)
set(CMAKE_CXX_STANDARD 20)
add_executable(main main.cpp)

find_package(glad CONFIG REQUIRED)
target_link_libraries(main PRIVATE glad::glad)

find_package(glfw3 CONFIG REQUIRED)
target_link_libraries(main PRIVATE glfw)
# ./vcpkg install freeglut
# find_package(GLUT REQUIRED)
# target_link_libraries(main PRIVATE GLUT::GLUT)


## ./vcpkg install glew
#find_package(GLEW REQUIRED)
#target_link_libraries(little_plane PRIVATE GLEW::GLEW)

#
# glm
# find_package(glm CONFIG REQUIRED)
# target_link_libraries(little_plane PRIVATE glm)

# ./vcpkg install libpng
# find_package(PNG REQUIRED)
# target_link_libraries(little_plane PRIVATE PNG::PNG)
##

# find_package(ZLIB REQUIRED)
# target_link_libraries(little_plane PRIVATE ZLIB::ZLIB)

find_package(OpenGL REQUIRED)

if (OPENGL_FOUND)
    message("opengl found")
    message("include dir: ${OPENGL_INCLUDE_DIR}")
    message("link libraries: ${OPENGL_gl_LIBRARY}")
else (OPENGL_FOUND)
    message("opengl not found")
endif()
target_link_libraries(main PRIVATE OpenGL::GL)