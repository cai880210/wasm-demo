cd build
emcmake cmake ..
emmake make

cmake .. -G "MinGW Makefiles" -DENABLE_CJSON_TEST=Off -DENABLE_SAFE_STACK=On -DBUILD_SHARED_AND_STATIC_LIBS=On -DCJSON_BUILD_SHARED_LIBS=On 
cmake .. -G "MinGW Makefiles" -DENABLE_CJSON_TEST=Off -DENABLE_SAFE_STACK=On -DBUILD_SHARED_AND_STATIC_LIBS=On -DCJSON_OVERRIDE_BUILD_SHARED_LIBS=On -DBUILD_SHARED_LIBS=On

cJOSN

-DENABLE_CJSON_TEST=On: Enable building the tests. (on by default)
-DENABLE_CJSON_UTILS=On: Enable building cJSON_Utils. (off by default)
-DENABLE_TARGET_EXPORT=On: Enable the export of CMake targets. Turn off if it makes problems. (on by default)
-DENABLE_CUSTOM_COMPILER_FLAGS=On: Enable custom compiler flags (currently for Clang, GCC and MSVC). Turn off if it makes problems. (on by default)
-DENABLE_VALGRIND=On: Run tests with valgrind. (off by default)
-DENABLE_SANITIZERS=On: Compile cJSON with AddressSanitizer and UndefinedBehaviorSanitizer enabled (if possible). (off by default)
-DENABLE_SAFE_STACK: Enable the SafeStack instrumentation pass. Currently only works with the Clang compiler. (off by default)
-DBUILD_SHARED_LIBS=On: Build the shared libraries. (on by default)
-DBUILD_SHARED_AND_STATIC_LIBS=On: Build both shared and static libraries. (off by default)
-DCMAKE_INSTALL_PREFIX=/usr: Set a prefix for the installation.
-DENABLE_LOCALES=On: Enable the usage of localeconv method. ( on by default )
-DCJSON_OVERRIDE_BUILD_SHARED_LIBS=On: Enable overriding the value of BUILD_SHARED_LIBS with -DCJSON_BUILD_SHARED_LIBS.
-DENABLE_CJSON_VERSION_SO: Enable cJSON so version. ( on by default )