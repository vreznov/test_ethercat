cmake_minimum_required(VERSION 3.5)

project(test2 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# add header floder
include_directories("/usr/include/soem/")

#aux_source_directory("/home/kare/文档/soft_pkg/soem131/SOEM-1.3.1/soem/" SRC_LIST)

#include_directories("/home/kare/文档/soft_pkg/soem131/SOEM-1.3.1/allsrc/")
#aux_source_directory("/home/kare/文档/soft_pkg/soem131/SOEM-1.3.1/allsrc/" SRC_LIST)

find_library(TESTFUNC_LIB1
    NAMES libsoem.a
    HINTS "/usr/lib/soem/")

find_library(TESTFUNC_LIB2
    NAMES liboshw.a
    HINTS "/usr/lib/soem/")

find_library(TESTFUNC_LIB3
    NAMES libosal.a
    HINTS "/usr/lib/soem/")

#set(CMAKE_EXE_LINKER_FLAGS “${CMAKE_EXE_LINKER_FLAGS}  -Wl,-Map,test2.map”)
#add_compile_options("-Wl, -Map=test2.map")

add_executable(test2 m2.cpp )
target_link_libraries (test2
    ${TESTFUNC_LIB1}
    ${TESTFUNC_LIB2}
    ${TESTFUNC_LIB3}
    pthread
    )

