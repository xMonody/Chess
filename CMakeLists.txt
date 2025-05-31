cmake_minimum_required(VERSION 3.16)
project(Chese LANGUAGES CXX)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

#set(CMAKE_CXX_STANDARD_LIBRARIES "-static -static-libgcc -static-libstdc++")
#set(CMAKE_CXX_FLAGS "-static -static-libgcc -static-libstdc++")
set(CMAKE_EXE_LINKER_FLAGS "-static -static-libgcc -static-libstdc++")

set(CMAKE_PREFIX_PATH "/mingw64/qt5-static")
# set(CMAKE_PREFIX_PATH D:/Library/qt5/lib/cmake)
# set(CMAKE_PREFIX_PATH D:/Library/qt5/lib/cmake/Qt5)

set(CMAKE_CXX_FLAGS -mwindows)

set(CMAKE_EXE_LINKER_FLAGS "-static")
set(CMAKE_CXX_COMPILE g++)
set(CMAKE_EXPORT_COMPILE_COMMANDS 1)

find_package(Qt5 REQUIRED COMPONENTS Core Gui Widgets)

add_executable(${PROJECT_NAME}
    board.cpp
    main.cpp
    stone.cpp
    util.cpp
    stone.h
    util.h
    board.h
   
)

target_link_libraries(${PROJECT_NAME} PUBLIC
    Qt::Core
    Qt::Gui
    Qt::Widgets
    -Wl,-Bstatic -lz -lzstd  # 强制静态链接 zlib 和 zstd
)
# 确保静态链接
#target_link_options(${PROJECT_NAME} PRIVATE
    #-static
    #-static-libgcc
    #-static-libstdc++
#)

#cmake ../ -DQt5Core_DIR="/mingw64/qt5-static/lib/cmake/Qt5Core" -DQt5Gui_DIR="/mingw64/qt5-static/lib/cmake/Qt5Gui" \
# -DQt5Widgets_DIR="/msys64/mingw64/qt5-static/lib/cmake/Qt5Widgets" -DQt5_DIR="/mingw64/qt5-static/lib/cmake/Qt5" -DCMAKE_BUILD_TYPE=Rleases

# Qt6
cmake_minimum_required(VERSION 3.25)

project(Chese LANGUAGES CXX)

# 开启 Qt6 自动处理特性
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)

#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -static -static-libgcc -static-libstdc++")
set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -static -static-libgcc -static-libstdc++")
# 明确使用静态 Qt6 安装路径
set(CMAKE_PREFIX_PATH "C:/msys64/mingw64/qt6-static")
set(Qt6_DIR "C:/msys64/mingw64/qt6-static/lib/cmake/Qt6")

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_package(Qt6 REQUIRED COMPONENTS Core Gui Widgets)

add_executable(${PROJECT_NAME}
    main.cpp
    mainwindow.cpp
    mainwindow.h
)

target_link_libraries(${PROJECT_NAME}
    Qt6::Core
    Qt6::Gui
    Qt6::Widgets
)


