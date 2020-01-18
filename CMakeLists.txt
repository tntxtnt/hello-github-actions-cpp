cmake_minimum_required(VERSION 3.10)

# Project name will also be executable name
project(cpp-hello-actions)

# Change your C++ standard here
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add your project header/source files here
set (${PROJECT_NAME}_sources
    src/main.cpp)
set (${PROJECT_NAME}_incldirs
    )
set (${PROJECT_NAME}_headers
    )
set (${PROJECT_NAME}_linklibs
    )

# Automatic
add_executable(${PROJECT_NAME}
    ${${PROJECT_NAME}_headers}
    ${${PROJECT_NAME}_sources})
target_include_directories(${PROJECT_NAME}
    PRIVATE ${${PROJECT_NAME}_incldirs})
target_link_libraries(${PROJECT_NAME}
    PRIVATE ${${PROJECT_NAME}_linklibs})
# UTF-8 encoding for MSVC
if (MSVC)
	target_compile_options(${PROJECT_NAME} PRIVATE "/utf-8")
endif()

# Tests
enable_testing()
add_test(NAME ${PROJECT_NAME} COMMAND ${PROJECT_NAME})
