cmake_minimum_required(VERSION 3.3)

set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

project(boost_regex)

option(BOOST_REGEX_SHARED_LIB "Enable dynamic linking" ON)

option(BOOST_REGEX_USE_ICU "Enable support for ICU" OFF)

option(BOOST_REGEX_USE_WREGEX "Enable support for Unicode regular expressions" OFF)

if(BOOST_REGEX_USE_ICU)
  find_package(ICU REQUIRED)
endif(BOOST_REGEX_USE_ICU)

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

if(BOOST_REGEX_USE_ICU)
  target_compile_definitions(boost_regex PUBLIC BOOST_HAS_ICU=1)
  target_link_libraries(boost_regex ICU::ICU)
endif(BOOST_REGEX_USE_ICU)

target_link_libraries(boost_regex
  boost::assert
  boost::concept_check boost::config boost::conversion boost::core
  boost::detail
  boost::function boost::function_types boost::functional boost::fusion
  boost::integer boost::iterator
  boost::mpl
  boost::optional
  boost::predef boost::preprocessor
  boost::smart_ptr boost::static_assert
  boost::throw_exception boost::tuple boost::type_index boost::type_traits boost::typeof
  boost::utility)

if(NOT BOOST_REGEX_USE_WREGEX)
target_compile_definitions(boost_regex PRIVATE BOOST_NO_WREGEX)
endif(NOT BOOST_REGEX_USE_WREGEX)

target_include_directories(boost_regex BEFORE PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)

install(TARGETS boost_regex DESTINATION lib)
install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/boost DESTINATION include)

add_library(boost::regex ALIAS boost_regex)
