cmake_minimum_required(VERSION 3.10)
project(onvif)

# Build core library
add_subdirectory(core)

# Set C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# App sources
set(APP_SOURCES
	app/main.cpp
	app/onvifptzcontrol.cpp
	app/onvifptzcontrol.h
)

# Add executable
add_executable(ipcamera ${APP_SOURCES})

# Include directories for app
target_include_directories(ipcamera PRIVATE
	${CMAKE_CURRENT_SOURCE_DIR}/core/include
	${CMAKE_CURRENT_SOURCE_DIR}/core/include/gsoap
	${CMAKE_CURRENT_SOURCE_DIR}/core/include/gsoap/plugin
)

# Link with core library and system libs
target_link_libraries(ipcamera PRIVATE onvifcore ssl crypto z)
