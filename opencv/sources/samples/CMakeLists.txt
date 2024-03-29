# Detect if we want to build samples with library binaries or not
if(NOT CMAKE_SOURCE_DIR STREQUAL CMAKE_CURRENT_LIST_DIR)
#
# BUILD CASE 1: Build samples with library sources
#


# ----------------------------------------------------------------------------
#  CMake file for samples. See root CMakeLists.txt
#
# ----------------------------------------------------------------------------

add_subdirectory(c)
add_subdirectory(cpp)
add_subdirectory(gpu)
add_subdirectory(ocl)

if(ANDROID AND BUILD_ANDROID_EXAMPLES)
  add_subdirectory(android)
endif()

if(INSTALL_C_EXAMPLES)
  install(FILES "CMakeLists.txt"
          DESTINATION ${OPENCV_SAMPLES_SRC_INSTALL_PATH}
          PERMISSIONS OWNER_READ OWNER_WRITE GROUP_READ WORLD_READ COMPONENT samples)
endif()

if(INSTALL_PYTHON_EXAMPLES)
  add_subdirectory(python2)
endif()

#
# END OF BUILD CASE 1: Build samples with library sources
#
else()
#
# BUILD CASE 2: Build samples with library binaries
#
cmake_minimum_required(VERSION 2.8)

project(samples C CXX)
option(BUILD_EXAMPLES "Build samples" ON)

find_package(OpenCV REQUIRED)

if(MSVC)
  add_definitions(-D_CRT_SECURE_NO_WARNINGS)

  if(NOT OpenCV_SHARED)
    foreach(flag_var
            CMAKE_C_FLAGS CMAKE_C_FLAGS_DEBUG CMAKE_C_FLAGS_RELEASE
            CMAKE_C_FLAGS_MINSIZEREL CMAKE_C_FLAGS_RELWITHDEBINFO
            CMAKE_CXX_FLAGS CMAKE_CXX_FLAGS_DEBUG CMAKE_CXX_FLAGS_RELEASE
            CMAKE_CXX_FLAGS_MINSIZEREL CMAKE_CXX_FLAGS_RELWITHDEBINFO)
      if(${flag_var} MATCHES "/MD")
        string(REGEX REPLACE "/MD" "/MT" ${flag_var} "${${flag_var}}")
      endif()
      if(${flag_var} MATCHES "/MDd")
        string(REGEX REPLACE "/MDd" "/MTd" ${flag_var} "${${flag_var}}")
      endif()
    endforeach(flag_var)

    set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} /NODEFAULTLIB:atlthunk.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:msvcrtd.lib")
    set(CMAKE_EXE_LINKER_FLAGS_DEBUG "${CMAKE_EXE_LINKER_FLAGS_DEBUG} /NODEFAULTLIB:libcmt.lib")
    set(CMAKE_EXE_LINKER_FLAGS_RELEASE "${CMAKE_EXE_LINKER_FLAGS_RELEASE} /NODEFAULTLIB:libcmtd.lib")
  endif()
endif()

add_subdirectory(c)
add_subdirectory(cpp)
ocv_check_dependencies(opencv_ocl)
if (OCV_DEPENDENCIES_FOUND)
  add_subdirectory(ocl)
endif()
ocv_check_dependencies(opencv_gpu)
if (OCV_DEPENDENCIES_FOUND)
  add_subdirectory(gpu)
endif()

#
# END OF BUILD CASE 2: Build samples with library binaries
#
endif()