cmake_minimum_required ( VERSION 2.8 )
project ( TPAvion )

MESSAGE(STATUS "OSG_ROOT = $ENV{OSG_ROOT}")
MESSAGE(STATUS "OSG_LIBRARY_PATH = $ENV{OSG_LIBRARY_PATH}")

#set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} $ENV{OSG_ROOT}/CMakeModules )
#MESSAGE(STATUS "CMAKE_MODULE_PATH = ${CMAKE_MODULE_PATH}")

set(SRCEXT "cpp")

file( GLOB_RECURSE
source_files
./src/*.${SRCEXT}
)

#find_package ( OSG )
find_package ( osg )
find_package ( osgDB )
find_package ( osgUtil )
find_package ( osgViewer )
find_package ( osgGA )
find_package ( OpenThreads )

MESSAGE(STATUS "OSG_INCLUDE_DIR = ${OSG_INCLUDE_DIR}")
INCLUDE_DIRECTORIES(${OSG_INCLUDE_DIR})

LINK_DIRECTORIES( ${OSG_LIB_DIR})

#augmentation
add_executable(tpavion ${source_files})

TARGET_LINK_LIBRARIES(tpavion ${OSG_LIBRARY} ${OSGGA_LIBRARY} ${OSGDB_LIBRARY} ${OSGUTIL_LIBRARY} ${OSGVIEWER_LIBRARY} ${OPENTHREADS_LIBRARY})

message("CMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}")

