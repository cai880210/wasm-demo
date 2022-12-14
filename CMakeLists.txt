cmake_minimum_required(VERSION 3.15) # 根据你的需求进行修改
project(sample C)

set(CMAKE_C_STANDARD 11) # 根据你的C编译器支持情况进行修改
set(CMAKE_EXECUTABLE_SUFFIX ".html") # 编译生成.html
set(CMAKE_C_FLAGS "-fno-stack-protector -U_FORTIFY_SOURCE")
include_directories(vendor) # 使得我们能引用第三方库的头文件
add_subdirectory(vendor/cJSON) # 编译外部包
add_library(cJSON STATIC vendor/cJSON/cJSON.c)
add_executable(sample main.c)
# 设置Emscripten的编译链接参数，我们等等会讲到一些常用参数
# link_directories(vendor/cJSON) 
set_target_properties(sample PROPERTIES LINK_FLAGS "\
-s EXIT_RUNTIME=1 \
-s EXPORTED_FUNCTIONS=\"['_json_parse', '_malloc']\" \
-s \"EXTRA_EXPORTED_RUNTIME_METHODS=['ccall', 'cwrap', 'malloc', '_malloc', 'intArrayFromString']\" \
-s ALLOW_MEMORY_GROWTH=1 \
")
target_link_libraries(sample cJSON) # 将第三方库与主程序进行链接