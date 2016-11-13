cmake_minimum_required(VERSION 3.6)
project(librpc)
set(SOURCE_FILES
        connection.cc
        connection.h
        fifo.h
        marshall.h
        method_thread.h
        jsl_log.h
        jsl_log.cc
        pollmgr.cc
        pollmgr.h
        rpc.cc
        rpc.h
        slock.h
        thr_pool.cc
        thr_pool.h
        )
include_directories(../)


add_library(rpc ${SOURCE_FILES})

link_libraries(rpc)
add_executable(rpctester rpctest.cc)