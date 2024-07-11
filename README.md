# openssl-dep

openssl-dep is a CMake module that downloads OpenSSL source code & compiles it with your project. For now it only plans to work on Unix-like OSs.

## How to Use:

It uses OpenSSL `3.3.1` by default. If you want to use previous vesions of OpenSSL, you should define this in your `CMakeLists.txt`:

```cmake
set(OPENSSL_DEP_NOT_USE_OPENSSL3 ON)
```

It will download OpenSSL `1.1.1w`.

And then:

```cmake
include(/path/to/openssl-dep.cmake)
```

openssl-dep configures OpenSSL on CMake configuration with the following parameters:

```
no-apps
no-docs
no-tests
```

Normally OpenSSL would not be compiled since it takes a lot of time, you should add target dependency like:

```cmake
add_dependencies(your_target compile_openssl)
```

and line include directory & libraries like:

```cmake
target_include_directories(your_target
    PRIVATE
        ${OPENSSL_DEP_INCLUDE_DIR}
)
target_link_libraries(your_target
    ${OPENSSL_DEP_LIBCRYPTO_PATH}
    ${OPENSSL_DEP_LIBSSL_PATH}
)
```
