# Maekathni's CMake C++ Project Template

This project template allows one to easily build and run multiple c++ executables and libraries with minimal setup.
It also is set to automatically generate the files needed for clangd, but it is not required.

## Basic Usage

### Setup
```
git clone LINK
cp -r {wherever you need it}
cd {copied directory}
rm -rf .git
git init
```

Finally update `project(CMakeDemo VERSION 1.0 LANGUAGES CXX)` in ./CMakeLists.txt for your project.

Then:
```
# Running ./build.sh is important
./build.sh  
```

### Run
```
./build.sh
```

### Add an executable 

> for example we will use 'runtime'

1. Make a directory called src/runtime - both cpp and headers files go here.
2. Make CMakeLists.txt in src/runtime
```
add_executable(runtime main.cpp)
target_link_libraries(runtime)

# if you need any internal library files:
#target_link_libraries(runtime PRIVATE examplelib)
```
3. In ./CMakeLists.txt
```
add_subdirectory(src/runtime)
```

### Add an library 

> for example we will use 'anotherexamplelib'

1. Make a directory called src/anotherexamplelib - this is where you .cpp files go.
2. Make a directory called src/anotherexamplelib/include/anotherexamplelib - header files go here.
3. Make CMakeLists.txt in src/anotherexamplelib
```
add_library(anotherexamplelib anotherexamplelib.cpp)

# Public include directory for consumers of the library
target_include_directories(anotherexamplelib
    PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include
)
```
4. In ./CMakeLists.txt
```
add_subdirectory(src/anotherexamplelib)
```

## MacOS
```zsh
# Required
brew install cmake

# Optional
brew install clangd
```

## File Tree
```
.
├── build.sh
├── CMakeLists.txt
├── README.md
└── src
    ├── app1
    │   ├── CMakeLists.txt
    │   └── main.cpp
    ├── app2
    │   ├── CMakeLists.txt
    │   └── main.cpp
    └── examplelib
        ├── CMakeLists.txt
        ├── examplelib.cpp
        └── include
            └── examplelib
                └── examplelib.h
```
