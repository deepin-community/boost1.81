cmake_minimum_required(VERSION 3.5)
project(Boost CXX)

FIND_PACKAGE(MPI REQUIRED)
INCLUDE_DIRECTORIES(${MPI_INCLUDE_PATH})

FIND_PACKAGE(Boost COMPONENTS graph_parallel mpi system REQUIRED)
INCLUDE_DIRECTORIES (${Boost_INCLUDE_DIRS})

ADD_EXECUTABLE(demo1 demo1.cpp)
TARGET_LINK_LIBRARIES(demo1 ${Boost_LIBRARIES} ${MPI_LIBRARIES})

ADD_EXECUTABLE(demo2 demo2.cpp)
TARGET_LINK_LIBRARIES(demo2 ${Boost_LIBRARIES} ${MPI_LIBRARIES})

FILE(COPY ${CMAKE_CURRENT_SOURCE_DIR}/weighted_graph.gr
        DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
