cmake_minimum_required(VERSION 3.4.0)
project(qlua_chm_ex1)

get_filename_component(TOP_DIR "${CMAKE_CURRENT_SOURCE_DIR}" PATH)
set(QLUACPP "${TOP_DIR}/contrib/qluacpp")
set(LUACPP "${TOP_DIR}/contrib/qluacpp/contrib/luacpp")
set(LUA "${TOP_DIR}/contrib/lua")
set(RWQUEUE "${TOP_DIR}/contrib/readerwriterqueue")

set(LUA_LIBRARIES "${LUA}/lua5.1.lib")
set(LUA_INCLUDE_DIR "${LUA}/include")

include_directories(
  ${QLUACPP}/include
  ${LUACPP}/include
  ${LUA_INCLUDE_DIR}
  ${RWQUEUE}
  )

set(SOURCES
  src/table_object.cpp
  src/quik_table_wrapper.cpp
)

# MSVC does not default to C++17 yet
if (MSVC_VERSION GREATER_EQUAL "1900")
  include(CheckCXXCompilerFlag)
  CHECK_CXX_COMPILER_FLAG("/std:c++17" _cpp_latest_flag_supported)
  if (_cpp_latest_flag_supported)
    add_compile_options("/std:c++17")
  endif()
endif()  

add_library(lualib_qlua_chm_ex1 SHARED ${SOURCES})

target_link_libraries(lualib_qlua_chm_ex1 ${LUA_LIBRARIES})

# Needed for Mingw
set_target_properties(lualib_qlua_chm_ex1 PROPERTIES CXX_STANDARD 17)
