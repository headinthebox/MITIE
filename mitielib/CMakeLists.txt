#
# This is a CMake makefile.  You can find the cmake utility and
# information about it at http://www.cmake.org
#

# setting this makes CMake allow normal looking if else statements
SET(CMAKE_ALLOW_LOOSE_LOOP_CONSTRUCTS true)

cmake_minimum_required(VERSION 2.4)

# Suppress cmake warnings about changes in new versions.
if(COMMAND cmake_policy) 
   cmake_policy(SET CMP0003 NEW) 
endif()


if (NOT TARGET mitie)
   include(../dlib/dlib/cmake)
   include_directories(include)

   set(source_files 
         src/stemmer.cpp
         src/stem.c
         )

   add_library(mitie ${source_files})
   target_link_libraries(mitie dlib)
endif()