cmake_minimum_required(VERSION 3.16)
project(testQt6QMLCpp LANGUAGES CXX C)

set(CMAKE_AUTOMOC ON)

find_package(Qt6 REQUIRED COMPONENTS Core Gui Qml Quick)

qt_add_executable(testQt6QMLCpp WIN32
    main.cpp
)

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    target_compile_definitions(testQt6QMLCpp PRIVATE QT_QML_DEBUG)
endif()

set_target_properties(testQt6QMLCpp PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY "bin"
    ARCHIVE_OUTPUT_DIRECTORY "lib"
    LIBRARY_OUTPUT_DIRECTORY "lib"
    WIN32_EXECUTABLE TRUE
)

target_link_libraries(testQt6QMLCpp PRIVATE
    Qt::Core
    Qt::Gui
    Qt::Qml
    Qt::Quick
)

qt_add_qml_module(testQt6QMLCpp
    URI testQt6QMLCpp
    VERSION 1.0
    QML_FILES
        "QML/main.qml"
        "QML/Scene.ui.qml"
    RESOURCES
        "QML/assets/torizon-logo.png"
)


