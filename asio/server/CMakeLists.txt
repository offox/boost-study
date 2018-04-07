
cmake_minimum_required(VERSION 2.6)

PROJECT(boost-asio-examples)

# Usage: 
#   cmake .. -DCMAKE_INCLUDE_PATH=/home/ott/exp/include -DCMAKE_LIBRARY_PATH=/home/ott/exp/lib
#       -DBOOST_INCLUDEDIR=/home/ott/exp/include -DBOOST_LIBRARYDIR=/home/ott/exp/lib
#

SET(Boost_USE_STATIC_LIBS OFF)
SET(Boost_USE_MULTITHREAD ON)

FIND_PACKAGE(Boost 1.42.0 REQUIRED COMPONENTS system thread regex)
IF(Boost_FOUND)
  INCLUDE_DIRECTORIES(${Boost_INCLUDE_DIRS})
  LINK_DIRECTORIES(${Boost_LIBRARY_DIRS})
ENDIF(Boost_FOUND)

SET(USED_LIBS ${Boost_SYSTEM_LIBRARY} ${Boost_THREAD_LIBRARY} ${Boost_REGEX_LIBRARY})

ADD_EXECUTABLE(server server.cpp)

TARGET_LINK_LIBRARIES(server ${USED_LIBS} pthread)

# FIND_PACKAGE( Boost 1.40 COMPONENTS program_options REQUIRED )

# INCLUDE_DIRECTORIES( ${Boost_INCLUDE_DIR} )

# ADD_EXECUTABLE( anyExecutable server.cpp )

# TARGET_LINK_LIBRARIES( anyExecutable LINK_PUBLIC ${Boost_LIBRARIES} pthread)
