cmake_minimum_required(VERSION 3.3)

project(boost_regex)

option(BOOST_REGEX_SHARED_LIB "Enable dynamic linking" ON)

set(SOURCE_FILES src/c_regex_traits.cpp
  src/cpp_regex_traits.cpp
  src/cregex.cpp
  src/fileiter.cpp
  src/icu.cpp
  src/instances.cpp
  src/posix_api.cpp
  src/regex.cpp
  src/regex_debug.cpp
  src/regex_raw_buffer.cpp
  src/regex_traits_defaults.cpp
  src/static_mutex.cpp
  src/w32_regex_traits.cpp
  src/wide_posix_api.cpp
  src/winstances.cpp
  src/usinstances.cpp)

if(BOOST_REGEX_SHARED_LIB)
  add_library(boost_regex SHARED ${SOURCE_FILES} )
  target_compile_definitions(boost_regex PRIVATE BOOST_REGEX_DYN_LINK=1)
else()
  add_library(boost_regex STATIC ${SOURCE_FILES})
  target_compile_definitions(boost_regex PRIVATE BOOST_REGEX_STATIC_LINK=1)
endif(BOOST_REGEX_SHARED_LIB)

target_include_directories(boost_regex BEFORE PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)
target_link_libraries(boost_regex
  boost_assert
  boost_concept_check boost_config boost_conversion boost_core
  boost_detail
  boost_function boost_function_types boost_functional boost_fusion
  boost_integer boost_iterator
  boost_mpl
  boost_optional
  boost_predef boost_preprocessor
  boost_smart_ptr boost_static_assert
  boost_throw_exception boost_tuple boost_type_index boost_type_traits boost_typeof
  boost_utility)

install(TARGETS boost_regex DESTINATION lib)
install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/boost DESTINATION include)
