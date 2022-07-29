cmake_minimum_required(VERSION 3.10)
project(Game)

set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++03")
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

file(GLOB SRC_FILES CONFIGURE_DEPENDS "*.h" "*.cpp")
# Detect and add SFML
set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake_modules" ${CMAKE_MODULE_PATH})

add_executable(Game ${SRC_FILES})

find_package(SFML 2 REQUIRED system graphics window network audio)
if (SFML_FOUND)
    include_directories(${SFML_INCLUDE_DIR})
    target_link_libraries(${PROJECT_NAME} ${SFML_LIBRARIES})
endif ()
