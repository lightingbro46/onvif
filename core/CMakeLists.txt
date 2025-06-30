cmake_minimum_required(VERSION 3.10)
project(onvifcore)

# Set C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Create the library target
add_library(onvifcore STATIC 
    # Source files
    src/gsoap/dom.cpp 
    src/gsoap/plugin/curlapi.cpp 
    src/gsoap/plugin/httpda.cpp 
    src/gsoap/plugin/httpform.cpp 
    src/gsoap/plugin/httpget.cpp 
    src/gsoap/plugin/httpmd5.cpp 
    src/gsoap/plugin/httppipe.cpp 
    src/gsoap/plugin/httppost.cpp 
    src/gsoap/plugin/logging.cpp 
    src/gsoap/plugin/md5evp.cpp 
    src/gsoap/plugin/mecevp.cpp 
    src/gsoap/plugin/mq.cpp 
    src/gsoap/plugin/plugin.cpp 
    src/gsoap/plugin/sessions.cpp 
    src/gsoap/plugin/smdevp.cpp 
    src/gsoap/plugin/threads.cpp 
    src/gsoap/plugin/wsaapi.cpp 
    src/gsoap/plugin/wsseapi.cpp 
    src/gsoap/stdsoap2.cpp 
    src/soapAdvancedSecurityServiceBindingProxy.cpp 
    src/soapC.cpp 
    src/soapDeviceBindingProxy.cpp 
    src/soapDeviceIOBindingProxy.cpp 
    src/soapImagingBindingProxy.cpp 
    src/soapMediaBindingProxy.cpp 
    src/soapPTZBindingProxy.cpp 
    src/soapPullPointSubscriptionBindingProxy.cpp 
    src/soapRemoteDiscoveryBindingProxy.cpp
)

# Header files (not mandatory to list, but can be included for IDE support)
target_sources(onvifcore PRIVATE
    include/gsoap/plugin/calcrest.h 
    include/gsoap/plugin/curlapi.h 
    include/gsoap/plugin/httpda.h 
    include/gsoap/plugin/httpform.h 
    include/gsoap/plugin/httpget.h 
    include/gsoap/plugin/httpmd5.h 
    include/gsoap/plugin/httppipe.h 
    include/gsoap/plugin/httppost.h 
    include/gsoap/plugin/logging.h 
    include/gsoap/plugin/md5evp.h 
    include/gsoap/plugin/mecevp.h 
    include/gsoap/plugin/mq.h 
    include/gsoap/plugin/plugin.h 
    include/gsoap/plugin/sessions.h 
    include/gsoap/plugin/smdevp.h 
    include/gsoap/plugin/threads.h 
    include/gsoap/plugin/wsaapi.h 
    include/gsoap/plugin/wsseapi.h 
    include/gsoap/plugin/wstapi.h 
    include/gsoap/stdsoap2.h 
    include/soapAdvancedSecurityServiceBindingProxy.h 
    include/soapDeviceBindingProxy.h 
    include/soapDeviceIOBindingProxy.h 
    include/soapH.h 
    include/soapImagingBindingProxy.h 
    include/soapMediaBindingProxy.h 
    include/soapPTZBindingProxy.h 
    include/soapPullPointSubscriptionBindingProxy.h 
    include/soapRemoteDiscoveryBindingProxy.h 
    include/soapStub.h 
    include/wsdd.nsmap
)

# Compiler definitions
target_compile_definitions(onvifcore PRIVATE 
    ONVIFCORE_LIBRARY 
    WITH_OPENSSL 
    WITH_DOM 
    WITH_ZLIB 
    WITH_COOKIES
)

# Include directories
target_include_directories(onvifcore PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/include
    ${CMAKE_CURRENT_SOURCE_DIR}/include/gsoap
    ${CMAKE_CURRENT_SOURCE_DIR}/include/gsoap/plugin
)

# Link libraries
target_link_libraries(onvifcore PRIVATE 
    crypto 
    ssl 
    z
)

# Output directories
set_target_properties(onvifcore PROPERTIES
    ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${CMAKE_CURRENT_BINARY_DIR}/debug
    ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${CMAKE_CURRENT_BINARY_DIR}/release
)
