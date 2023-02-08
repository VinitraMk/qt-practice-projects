cmake_minimum_required(VERSION 3.16)

project(FirstQtQuick VERSION 0.1 LANGUAGES CXX)

set(CMAKE_AUTOMOC ON)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt6 6.2 COMPONENTS Quick REQUIRED)

qt_add_executable(appFirstQtQuick
    main.cpp
)

qt_add_qml_module(appFirstQtQuick
    URI FirstQtQuick
    VERSION 1.0
    QML_FILES main.qml Page.qml
    RESOURCES qt-logo.png
)

set_target_properties(appFirstQtQuick PROPERTIES
    MACOSX_BUNDLE_GUI_IDENTIFIER my.example.com
    MACOSX_BUNDLE_BUNDLE_VERSION ${PROJECT_VERSION}
    MACOSX_BUNDLE_SHORT_VERSION_STRING ${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}
    MACOSX_BUNDLE TRUE
    WIN32_EXECUTABLE TRUE
)

target_link_libraries(appFirstQtQuick
    PRIVATE Qt6::Quick)

install(TARGETS appFirstQtQuick
    BUNDLE DESTINATION .
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR})
