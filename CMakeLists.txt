cmake_minimum_required(VERSION 3.10)

project(Factorio-TAS-Generator)

# dependencies

# set(wxBUILD_TOOLKIT gtk3)
# set(wxBUILD_SHARED off)
# add_subdirectory(libs/wxWidgets)

find_package(wxWidgets 3.2 COMPONENTS core base aui REQUIRED CONFIG)

# sources
set(SRC_FILES
    "src/Shared functions/Functions.cpp"
    "src/Shared functions/StringFunctions.cpp"
    "src/TAS save file/OpenTas.cpp"
    "src/TAS save file/SaveTas.cpp"
    src/AutoSaver.cpp
    src/cApp.cpp
    src/cMain_Focus.cpp
    src/cMain_Highlighter.cpp
    src/cMain.cpp
    src/CommandStack.cpp
    src/DialogProgressBar.cpp
    src/GenerateScript.cpp
    src/GUI_Base.cpp
    src/ImportStepsPanel.cpp
    src/Item.cpp
    src/Recipe.cpp
    src/SearchUtil.cpp
    src/ShortcutChanger.cpp
    src/StdUtil.cpp
    src/SteptypeColour.cpp
    src/Structures/Building.cpp
    src/Structures/Step.cpp
    src/Technology.cpp
    src/TemplatePage.cpp
    src/TypePanel.cpp
    src/WalkPanel.cpp
)

# build target for the executable
add_executable(${PROJECT_NAME} WIN32 MACOSX_BUNDLE ${SRC_FILES})
target_link_libraries(${PROJECT_NAME} ${wxWidgets_LIBRARIES})

# target_link_libraries(${PROJECT_NAME} wx::core wx::base wx::aui)

# c++ 20 support
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_20)