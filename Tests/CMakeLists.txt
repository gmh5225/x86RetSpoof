set(THREADS_PREFER_PTHREAD_FLAG ON)

find_package(Threads REQUIRED)

include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/refs/tags/release-1.11.0.zip
  URL_HASH SHA256=353571c2440176ded91c2de6d6cd88ddd41401d14692ec1f99e35d013feda55a
)

set(BUILD_GMOCK OFF CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

add_executable(Tests FastcallTests.cpp ThiscallTests.cpp StdcallTests.cpp CdeclTests.cpp)
target_link_libraries(Tests gtest_main Threads::Threads)

include(GoogleTest)
gtest_discover_tests(Tests)
