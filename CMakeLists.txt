PROJECT(pvr.hts)

CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

ENABLE_LANGUAGE(CXX)

FIND_PACKAGE(xbmc REQUIRED)
FIND_PACKAGE(xbmcplatform REQUIRED)

addon_version(pvr.hts HTS)

INCLUDE_DIRECTORIES(${xbmcplatform_INCLUDE_DIRS}
                    ${XBMC_INCLUDE_DIR}
                    ${PROJECT_SOURCE_DIR}/lib)

ADD_DEFINITIONS(-DUSE_DEMUX)

SET(SOURCES src/CircBuffer.cpp
            src/client.cpp
            src/GUIDialogTranscode.cpp
            src/HTSPConnection.cpp
            src/HTSPData.cpp
            src/HTSPDemux.cpp)

ADD_SUBDIRECTORY(lib/libhts)

SET(DEPLIBS ${xbmcplatform_LIBRARIES} hts)

build_addon(pvr.hts SOURCES DEPLIBS HTS_VERSION)
install_addon(pvr.hts ${HTS_VERSION})
