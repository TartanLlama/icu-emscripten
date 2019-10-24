# icu-emscripten
This repository contains headers and prebuilt libraries for ICU4C version 65.1, built with EMSDK version 1.38.48.

You can find the license for ICU [here](https://github.com/unicode-org/icu/blob/master/icu4c/LICENSE).

## Usage
If you have a CMake build system, you can use these binaries and headers like so:

```cmake
if(CMAKE_SYSTEM_NAME STREQUAL "Emscripten")
  include(FetchContent)
  FetchContent_Declare(
    icu-emscripten
    GIT_REPOSITORY https://github.com/TartanLlama/icu-emscripten.git
    GIT_TAG        master
  )
  FetchContent_MakeAvailable(icu-emscripten)

  # Make sure CMake doesn't try to pull in system installations of ICU
  set(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY NEVER)
  set(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE NEVER)
  set(ICU_ROOT ${icu-emscripten_SOURCE_DIR})
endif()

# Now we can use the FindICU module which CMake ships
find_package(ICU COMPONENTS uc dt REQUIRED)
```
