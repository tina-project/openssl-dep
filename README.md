# openssl-dep

openssl-dep is a CMake module that adds OpenSSL v3 dependency to your project.

## How to Use:

It uses OpenSSL `3.3.1`. Include this module in your project with:

```cmake
include(/path/to/openssl-dep.cmake)
```

On Unix-like OSs, openssl-dep configures OpenSSL on CMake configuration with the following parameters:

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

On Windows, a pre-compiled binary package is provided [here](./bin/OpenSSL-3.3.1-MinGW_W64.zip). The configuration command is:

```sh
./Configuration mingw64 no-apps no-docs no-tests --prefix=/openssl/3.3.1
```

It will directly extract the compiled binary package to `_deps/` directory. You can use the headers & the libraries just like how you do by Unix-like Oss.

## LICENSE

This module is open-sourced under the [MIT License](./LICENSE).
