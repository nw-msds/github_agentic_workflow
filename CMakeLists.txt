cmake_minimum_required(VERSION 3.20)
project(cpp_project)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Enable testing
enable_testing()

# Include directories
include_directories(
  ${crow_SOURCE_DIR}/include
  ${asio_SOURCE_DIR}/asio/include
)

# Main app
add_executable(cpp_project src/main.cpp)

# Tests
add_executable(test_project tests/test_main.cpp)
find_package(GTest REQUIRED)
target_link_libraries(test_project PRIVATE GTest::GTest pthread)

add_test(NAME SampleTest COMMAND test_project)