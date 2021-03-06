cmake_minimum_required(VERSION 2.6)

PROJECT(AIVI-Lab3)

IF(NOT CMAKE_BUILD_TYPE)
  SET(CMAKE_BUILD_TYPE "Debug" CACHE STRING "CMAKE_BUILD_TYPE: Choose the type of build, options are: None(CMAKE_CXX_FLAGS or CMAKE_C_FLAGS used) Debug Release RelWithDebInfo MinSizeRel." FORCE)
ENDIF(NOT CMAKE_BUILD_TYPE)

FIND_PACKAGE(OpenCV REQUIRED)
INCLUDE_DIRECTORIES(${OpenCV_INCLUDE_DIR})
INCLUDE_DIRECTORIES(${OpenCV_INCLUDE_DIRS})

ADD_DEFINITIONS(-Wall -std=c++11)

ADD_EXECUTABLE(Lab4 lab4.cpp Classifier.cpp Classifier.hpp) 
TARGET_COMPILE_OPTIONS(Lab4 PUBLIC -fPIC -Wall -Wno-sign-compare -Wno-uninitialized -O3 -DNDEBUG -DUSE_OPENCV)
TARGET_LINK_LIBRARIES(Lab4  /usr/lib/x86_64-linux-gnu/libcaffe.so.1.0.0-rc4 -L/usr/lib/x86_64-linux-gnu -lboost_system -lboost_thread -lboost_filesystem -lboost_chrono -lboost_date_time -lboost_atomic -lpthread -lpthread -lglog -lgflags -lprotobuf -lhdf5_cpp /usr/lib/x86_64-linux-gnu/hdf5/serial/libhdf5.so -lpthread -lpthread -lglog -lgflags -lprotobuf -lhdf5_cpp /usr/lib/x86_64-linux-gnu/hdf5/serial/libhdf5.so -lsz -lz -ldl -lm -lhdf5_hl_cpp /usr/lib/x86_64-linux-gnu/hdf5/serial/libhdf5_hl.so -llmdb -lleveldb -lsnappy -lcudart -lcurand -lcublas -Wl,-Bstatic -lcublas_device -Wl,-Bdynamic ${OpenCV_LIBS})

ADD_EXECUTABLE(Classification classification.cpp ) 
TARGET_COMPILE_OPTIONS(Classification PUBLIC -fPIC -Wall -Wno-sign-compare -Wno-uninitialized -O3 -DNDEBUG -DUSE_OPENCV)
TARGET_LINK_LIBRARIES(Classification  /usr/lib/x86_64-linux-gnu/libcaffe.so.1.0.0-rc4 -L/usr/lib/x86_64-linux-gnu -lboost_system -lboost_thread -lboost_filesystem -lboost_chrono -lboost_date_time -lboost_atomic -lpthread -lpthread -lglog -lgflags -lprotobuf -lhdf5_cpp /usr/lib/x86_64-linux-gnu/hdf5/serial/libhdf5.so -lpthread -lpthread -lglog -lgflags -lprotobuf -lhdf5_cpp /usr/lib/x86_64-linux-gnu/hdf5/serial/libhdf5.so -lsz -lz -ldl -lm -lhdf5_hl_cpp /usr/lib/x86_64-linux-gnu/hdf5/serial/libhdf5_hl.so -llmdb -lleveldb -lsnappy -lcudart -lcurand -lcublas -Wl,-Bstatic -lcublas_device -Wl,-Bdynamic ${OpenCV_LIBS})
