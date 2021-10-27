---
title: "Getting Started With Gtest"
date: 2021-10-27T09:46:58+02:00
categories: [testing]
tags: [c]
featured: true

draft: false
---

In this post we will have a brief introduction to the Google test library that will allow us to tests our C/C++ programs.


## Installing and compiling the Gtest library

- First, we need to install the library:

`sudo apt-get install libgtest-dev`

- We compile using cmake:

`cd /usr/src/gtest`

`sudo cmake CMakeLists.txt`

`sudo make`
 
- We copy libgtest.a and libgtest_main.a to /usr/lib:

`sudo cp *.a /usr/lib`

## Getting started

We will start with a very simple function:

```
unsigned int factorial(int num) {
 if (n == 0){
        return 1;
    }else{
        return(n * factorial(n-1));
    }
}
```

The tests.cpp code:
```
#include "factorial.cpp"
#include <gtest/gtest.h>

TEST(factorialTest, factorial_three) { 
    ASSERT_EQ(6, factorial(3));
}

```
And the CMakeLists.txt file:
```
cmake_minimum_required(VERSION 2.6)

# Set the project here.
project(Laboratory2)

# Locate GTest
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})
 
# Link runTests with what we want to test and the GTest and pthread library
add_executable(runTests tests.cpp)
target_link_libraries(runTests ${GTEST_LIBRARIES} pthread)
```

- Next, we can compile the code:


`cmake -S . -B build`

`cmake --build build`

`cd build && ctest`


- And finally we can run the tests:

`./runTests` 

### References

[GTest documentation](https://google.github.io/googletest/quickstart-cmake.html)
