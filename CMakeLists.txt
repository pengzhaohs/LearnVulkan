CMAKE_MINIMUM_REQUIRED(VERSION 3.1.0 FATAL_ERROR)

PROJECT(LearnVulkan)

SET(ZS_QT_ROOT "${ZS_QT_ROOT}" CACHE PATH "Please select the matched QT build root dir!")

IF(EXISTS ${ZS_QT_ROOT})
    SET(CMAKE_PREFIX_PATH "${ZS_QT_ROOT};${CMAKE_PREFIX_PATH}")
ELSE()
    MESSAGE(FATAL_ERROR "Please specify the ZS_QT_ROOT")
ENDIF()

SET(ZS_THIRDPARTY_ROOT "${ZS_THIRDPARTY_ROOT}" CACHE PATH "Please select the matched thirdparty root dir!")

IF(EXISTS ${ZS_THIRDPARTY_ROOT})
    SET(CMAKE_PREFIX_PATH "${ZS_THIRDPARTY_ROOT};${CMAKE_PREFIX_PATH}")
ELSE()
    MESSAGE(FATAL_ERROR "Please specify the ZS_THIRDPARTY_ROOT")
ENDIF()

SET(ZS_CMAKEMODULES_ROOT "${ZS_CMAKEMODULES_ROOT}" CACHE PATH "Please select the matched cmakemodules root dir!")

IF(EXISTS ${ZS_CMAKEMODULES_ROOT})
    SET(CMAKE_PREFIX_PATH "${ZS_CMAKEMODULES_ROOT};${CMAKE_PREFIX_PATH}")
ELSE()
    MESSAGE(FATAL_ERROR "Please specify the ZS_CMAKEMODULES_ROOT")
ENDIF()

MESSAGE("ZS_QT_ROOT=${ZS_QT_ROOT}")
MESSAGE("ZS_THIRDPARTY_ROOT=${ZS_THIRDPARTY_ROOT}")
MESSAGE("ZS_CMAKEMODULES_ROOT=${ZS_CMAKEMODULES_ROOT}")

SET(CMAKE_MODULE_PATH "${ZS_CMAKEMODULES_ROOT};${CMAKE_SOURCE_DIR};${CMAKE_MODULE_PATH}")

SET(ZS_ROOT_DIR ${CMAKE_SOURCE_DIR})
SET(ZS_SOURCE_DIR ${ZS_ROOT_DIR}/source)

INCLUDE(ZSoftPlatformDetermine)
INCLUDE(ZSoftMacroUtils)
INCLUDE(ZSoftGlobalSetting)
INCLUDE(ZSoftApplySetting)

SET(CMAKE_CXX_STANDARD 17)

FIND_PACKAGE(GLFW3 REQUIRED)
FIND_PACKAGE(GLM REQUIRED)
FIND_PACKAGE(VULKAN REQUIRED)

ADD_SUBDIRECTORY(source)

INCLUDE(CPack)




