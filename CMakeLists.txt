cmake_minimum_required(VERSION 3.16)
project(Chese LANGUAGES CXX)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_PREFIX_PATH D:/Library/qt5/lib/cmake)
set(CMAKE_PREFIX_PATH D:/Library/qt5/lib/cmake/Qt5)
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
)
