cmake_minimum_required(VERSION 3.16)

project(Network-app)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Set Qt version
set(QT_VERSION_MAJOR 6)
set(QT_VERSION_MINOR 0)

# Find Qt packages
find_package(Qt6 COMPONENTS 
    Core 
    Gui 
    Widgets 
    Network 
    LinguistTools
    REQUIRED
)

# Enable automoc, autorcc, and autouic
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

# Set MOC includes path
set(CMAKE_INCLUDE_CURRENT_DIR ON)

# Source files
set(SOURCES
    main.cpp
    mainwindow.cpp
    ChatPanel.cpp
    ChessBoard.cpp
    NetworkClient.cpp
    NetworkServer.cpp
    PromotionDialog.cpp
    StatusPanel.cpp
)

# Header files
set(HEADERS
    mainwindow.h
    ChatPanel.h
    ChessBoard.h
    ChessPiece.h
    NetworkClient.h
    NetworkServer.h
    PromotionDialog.h
    StatusPanel.h
    Bishop.h
    King.h
    Knight.h
    Pawn.h
    Queen.h
    Rook.h
)

# UI files
set(UI_FILES
    mainwindow.ui
)

# Resource files
set(RESOURCE_FILES
    resource.qrc
)

# Translation files
set(TRANSLATION_FILES
    Network-app_en_US.ts
)

# Create executable
add_executable(${PROJECT_NAME}
    ${SOURCES}
    ${HEADERS}
    ${UI_FILES}
    ${RESOURCE_FILES}
)

# Link Qt libraries
target_link_libraries(${PROJECT_NAME}
    Qt6::Core
    Qt6::Gui
    Qt6::Widgets
    Qt6::Network
)

# Handle translations
# Create translation files
# qt6_create_translation(QM_FILES 
#     ${CMAKE_CURRENT_SOURCE_DIR}
#     ${TRANSLATION_FILES}
# )

# Create a custom target for translations
# add_custom_target(translations ALL DEPENDS ${QM_FILES})
# add_dependencies(${PROJECT_NAME} translations)

# Optional: Set output directory
set_target_properties(${PROJECT_NAME} PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)

# Optional: For Windows, set the application properties
if(MSVC)
    set_target_properties(${PROJECT_NAME} PROPERTIES
        WIN32_EXECUTABLE ON
    )
endif()
