project(pvr.hts)

cmake_minimum_required(VERSION 2.6)

enable_language(CXX)

find_package(xbmc REQUIRED)
find_package(xbmcplatform REQUIRED)

include_directories(${xbmcplatform_INCLUDE_DIRS}
                    ${XBMC_INCLUDE_DIR}
                    ${PROJECT_SOURCE_DIR}/lib)

add_definitions(-DUSE_DEMUX)

set(HTS_SOURCES src/CircBuffer.cpp
                src/client.cpp
                src/GUIDialogTranscode.cpp
                src/HTSPConnection.cpp
                src/HTSPData.cpp
                src/HTSPDemux.cpp)

add_subdirectory(lib/libhts)

set(DEPLIBS ${xbmcplatform_LIBRARIES} hts)

build_addon(pvr.hts HTS DEPLIBS)

include(CPack)
