cmake_minimum_required(VERSION 3.15.0)

project(Qt-OpenGL-Fonts-with-Freetype-Library VERSION 0.1.0 LANGUAGES C CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(QT NAMES Qt6 REQUIRED COMPONENTS Widgets)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Widgets OpenGLWidgets Multimedia) # 
find_package(Freetype REQUIRED)

add_executable(fontLoad 
    main.cpp

    mainwidget.cpp
    mainwidget.h
    
    fontprovider.cpp
    fontprovider.h
   
    shaders.qrc
    )

target_link_libraries(fontLoad PRIVATE 
    Qt${QT_VERSION_MAJOR}::Widgets  
    Qt${QT_VERSION_MAJOR}::OpenGLWidgets 
    Qt${QT_VERSION_MAJOR}::Multimedia 
    ${FREETYPE_LIBRARIES})

target_include_directories(fontLoad PRIVATE  
    ./ 
    ${FREETYPE_INCLUDE_DIRS})