cmake_minimum_required(VERSION 3.10.0)
project(detect VERSION 0.1.0 LANGUAGES C CXX)

# Find OpenCV, you may need to set OpenCV_DIR variable
# to the absolute path to the directory containing OpenCVConfig.cmake file
# via the command line or GUI
find_package(OpenCV REQUIRED)

# If the package has been found, several variables will
# be set, you can find the full list with descriptions
# in the OpenCVConfig.cmake file.
# Print some message showing some of them
message(STATUS "OpenCV library status:")
message(STATUS "    config: ${OpenCV_DIR}")
message(STATUS "    version: ${OpenCV_VERSION}")
message(STATUS "    libraries: ${OpenCV_LIBS}")
message(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")


file(GLOB SOURCES "src/*.cpp")
# Declare the executable target built from your sources
add_executable(detect ${SOURCES})

target_include_directories(detect PRIVATE ${CMAKE_SOURCE_DIR}/include)
# Link your application with OpenCV libraries
target_link_libraries(detect PRIVATE ${OpenCV_LIBS})