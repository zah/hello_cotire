cmake_minimum_required(VERSION 2.8.0)
set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake")

project(CotireTest)

include(cotire)

add_executable(hello_cotire precompiled.cpp main.cpp precompiled.h)

set_target_properties(hello_cotire PROPERTIES COTIRE_ADD_UNITY_BUILD FALSE)
set_target_properties(hello_cotire PROPERTIES COTIRE_ENABLE_PRECOMPILED_HEADER TRUE)
set_target_properties(hello_cotire PROPERTIES COTIRE_CXX_PREFIX_HEADER_INIT "precompiled.h")

cotire(hello_cotire)

get_target_property(_prefix hello_cotire COTIRE_CXX_PREFIX_HEADER)
get_target_property(_precompiled hello_cotire COTIRE_CXX_PRECOMPILED_HEADER)

message("prefix " ${_prefix})
message("precompiled " ${_precompiled})
