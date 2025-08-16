add_library(examplelib examplelib.cpp)

# Public include directory for consumers of the library
target_include_directories(examplelib
    PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include
)

