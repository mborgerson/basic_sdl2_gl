cmake_minimum_required (VERSION 2.6)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake")
project (sdl_app)

# Main Executable
add_definitions("-Wall -Werror -O0 -g")
add_executable(sdl_app main.c)
target_include_directories(sdl_app PUBLIC ${CMAKE_SOURCE_DIR}/src)

# SDL2
find_package(SDL2 REQUIRED)
target_link_libraries(sdl_app ${SDL2_LIBRARY})
target_include_directories(sdl_app PUBLIC ${SDL2_INCLUDE_DIR})

# OpenGL
find_package(OpenGL REQUIRED)
target_link_libraries(sdl_app ${OPENGL_gl_LIBRARY})
target_include_directories(sdl_app PUBLIC ${OPENGL_INCLUDE_DIR})

# GL Extension Wrangler (GLEW)
find_package(GLEW REQUIRED)
target_link_libraries(sdl_app ${GLEW_LIBRARIES})
target_include_directories(sdl_app PUBLIC ${GLEW_INCLUDE_DIRS})
