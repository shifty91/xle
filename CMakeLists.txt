cmake_minimum_required(VERSION 2.6)
project(xle)

set(SRCS
  main.c
)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -std=gnu99 -pedantic -Wall -march=native")
set(CMAKE_BUILD_TYPE "Release")

# Search OpenSSL
find_package(X11 REQUIRED)

if (X11_FOUND)
  include_directories(${X11_INCLUDE_DIR})
  link_directories(${X11_LIBRARY_DIR})
endif()

add_executable(xle ${SRCS})
target_link_libraries(xle ${X11_LIBRARIES})
install(TARGETS xle DESTINATION bin COMPONENT binaries)
