cmake_minimum_required(VERSION 3.1)
project(subdirectory_sample CXX)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_POSITION_INDEPENDENT_CODE ON)

# find_package(Boost REQUIRED COMPONENTS random python numpy)
find_package(Boost REQUIRED COMPONENTS random)
message(STATUS "  Boost_INCLUDE_DIR=${Boost_INCLUDE_DIR}")
message(STATUS "  Boost_LIBRARY_DIR=${Boost_LIBRARY_DIR}")
message(STATUS "  Boost_LIBRARIES  =${Boost_LIBRARIES}")
include_directories("${Boost_INCLUDE_DIRS}")
link_directories("${Boost_LIBRARY_DIR}")
message(STATUS "BOOST_ROOT=${BOOST_ROOT}")
set(Boost_USE_STATIC_LIBS ON)
set(Boost_USE_MULTITHREADED ON)

find_package(CURL REQUIRED)
message(STATUS "  CURL_LIBRARIES  =${CURL_INCLUDE_DIR}")
include_directories(${CURL_INCLUDE_DIR})

add_executable(random_agent random_agent.cpp gym_binding.cpp jsoncpp.cpp)

target_link_libraries(random_agent ${Boost_LIBRARIES} curl)
