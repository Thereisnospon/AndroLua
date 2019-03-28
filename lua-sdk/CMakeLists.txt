cmake_minimum_required(VERSION 3.4.1)
#设置编译指令
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++11 -std=c++11 -fno-rtti -fno-exceptions -Wall")


aux_source_directory(src/main/jni/lua LUA_DIR)
aux_source_directory(src/main/jni/luajava LUA_JAVA_DIR)

include_directories(src/main/jni/lua)

add_library(lua SHARED ${LUA_DIR})
add_library(luajava SHARED ${LUA_JAVA_DIR})

target_link_libraries(luajava lua)
#
#add_library(myjni-lib SHARED
#        src/main/jni/jni_book_ch3.cpp
#        src/main/jni/jni_reflect.cpp
#        src/main/jni/Java2CppBridge.cpp
#        src/main/jni/Java2CppBridge.h
#        src/main/jni/log.h
#        )
#
#
#add_library(supermethodutil SHARED
#        src/main/jni/boxunbox.h
#        src/main/jni/boxunbox.cpp
#        src/main/jni/super_method.cpp
#        src/main/jni/log.h
#        )
#
## 从系统库中查找依赖库
#find_library( # Sets the name of the path variable.
#        # 设置依赖库的名字，下面链接库的时候会用到
#        log-lib
#
#        # Specifies the name of the NDK library that
#        # you want CMake to locate.
#
#        # 查找log依赖库
#        # {sdk-path}/ndk-bundle/sysroot/usr/include/android/log.h
#        log )
#
## 配置库的依赖关系(链接关系)
#target_link_libraries( # Specifies the target library.
#        # 目标库
#        myjni-lib
#
#        # Links the target library to the log library
#        # included in the NDK.
#        # 依赖库，可以是多个
#        ${log-lib} )
#
## 配置库的依赖关系(链接关系)
#target_link_libraries( # Specifies the target library.
#        # 目标库
#        supermethodutil
#
#        # Links the target library to the log library
#        # included in the NDK.
#        # 依赖库，可以是多个
#        ${log-lib} )