cmake_minimum_required (VERSION 3.2 FATAL_ERROR)
project (spinnaker-example)

set (CMAKE_CXX_STANDARD_REQUIRED ON)
set (CMAKE_CXX_STANDARD 17)

set(SPINNAKER_INCLUDE_DIR "/usr/include/spinnaker" CACHE PATH "Spinnaker Include Directory")

include_directories(
        ${SPINNAKER_INCLUDE_DIR}
)

find_library(SPINNAKER_LIB libSpinnaker.so)
find_library(SPINVIDEO_LIB libSpinVideo.so)

if(SPINNAKER_LIB)
    message(STATUS "Found SPINNAKER_LIB FlyCapture/Spinnaker lib ${PGR_LIB}")
else()
    message(FATAL_ERROR "Error! Could not find PGR FlyCapture/Spinnaker lib at ${PGR_DIR}!")
endif()

# add the executable
add_executable(Acquisition Acquisition.cpp)
target_link_libraries (Acquisition ${SPINNAKER_LIB})

add_executable(AcquisitionMultipleCamera AcquisitionMultipleCamera.cpp)
target_link_libraries (AcquisitionMultipleCamera ${SPINNAKER_LIB})

add_executable(Enumeration Enumeration.cpp)
target_link_libraries (Enumeration ${SPINNAKER_LIB})

add_executable(NodeMapInfo NodeMapInfo.cpp)
target_link_libraries (NodeMapInfo ${SPINNAKER_LIB})

add_executable(ImageFormatControl ImageFormatControl.cpp)
target_link_libraries (ImageFormatControl ${SPINNAKER_LIB})

add_executable(Exposure Exposure.cpp)
target_link_libraries (Exposure ${SPINNAKER_LIB})

add_executable(ExceptionHandling ExceptionHandling.cpp)
target_link_libraries (ExceptionHandling ${SPINNAKER_LIB})

add_executable(SaveToAvi SaveToAvi.cpp)
target_link_libraries (SaveToAvi ${SPINNAKER_LIB} ${SPINVIDEO_LIB})


