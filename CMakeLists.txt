cmake_minimum_required(VERSION 3.16)
project(OnlineExamSystem)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_AUTOMOC ON)

find_package(CURL REQUIRED)
find_package(Qt6 REQUIRED COMPONENTS Widgets)

include_directories(include)

file(GLOB SOURCES "src/*.cpp")

# Console version (keeps working)
add_executable(OnlineExamSystem main.cpp ${SOURCES})
target_link_libraries(OnlineExamSystem CURL::libcurl)

# Qt GUI version
file(GLOB GUI_SOURCES "gui/*.cpp")
add_executable(OnlineExamGUI ${GUI_SOURCES} ${SOURCES})
target_include_directories(OnlineExamGUI PRIVATE gui)
target_link_libraries(OnlineExamGUI CURL::libcurl Qt6::Widgets)
