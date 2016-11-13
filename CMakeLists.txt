cmake_minimum_required(VERSION 3.6)
project(yfs_class)
set(YFS_INCLUDE_PATH ./ rpc)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(SOURCE_FILES
    lang/algorithm.h
    lang/verify.h
    lock_protocol.h
)

set(LOCK_TEST_SOURCE
        lock_tester.cc
        )

add_subdirectory(rpc)

include_directories(${YFS_INCLUDE_PATH})
link_directories(rpc)
link_libraries(rpc)

#add_executable(yfs_class ${SOURCE_FILES})
add_executable(lock_client ${SOURCE_FILES} lock_client.cc lock_server.cc lock_smain.cc)
add_executable(lock_server ${SOURCE_FILES} lock_server.cc lock_smain.cc)
add_executable(lock_demo  ${SOURCE_FILES}  lock_demo.cc lock_client.cc lock_server.cc)
add_executable(lock_tester ${LOCK_TEST_SOURCE} lock_client.cc )
