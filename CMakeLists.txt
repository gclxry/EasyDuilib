########### https://cmake.org/cmake/help/v3.5/command/cmake_minimum_required.html
cmake_minimum_required (VERSION 3.5 FATAL_ERROR)


########### https://cmake.org/cmake/help/v3.5/command/project.html
project (duilib VERSION 1.0.0.1)


########### set mt md for gtest
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MT")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MTd")


########### use unicode
add_definitions(-D_UNICODE)


########### export symbols
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include/Control)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include/Core)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include/Layout)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include/Utils)

########### https://cmake.org/cmake/help/v3.5/command/add_library.html
set(duilib_sources 
"include/Control/UIActiveX.h"
"include/Control/UIButton.h"
"include/Control/UICheckBox.h"
"include/Control/UICombo.h"
"include/Control/UIDateTime.h"
"include/Control/UIEdit.h"
"include/Control/UIGifAnim.h"
"include/Control/UILabel.h"
"include/Control/UIList.h"
"include/Control/UIOption.h"
"include/Control/UIProgress.h"
"include/Control/UIRichEdit.h"
"include/Control/UIScrollBar.h"
"include/Control/UISlider.h"
"include/Control/UIText.h"
"include/Control/UITreeView.h"
"include/Control/UIWebBrowser.h"
"include/Core/UIBase.h"
"include/Core/UIContainer.h"
"include/Core/UIControl.h"
"include/Core/UIDefine.h"
"include/Core/UIDlgBuilder.h"
"include/Core/UIManager.h"
"include/Core/UIMarkup.h"
"include/Core/UIRender.h"
"include/Layout/UIChildLayout.h"
"include/Layout/UIHorizontalLayout.h"
"include/Layout/UITabLayout.h"
"include/Layout/UITileLayout.h"
"include/Layout/UIVerticalLayout.h"
"include/Utils/downloadmgr.h"
"include/Utils/FlashEventHandler.h"
"include/Utils/stb_image.h"
"include/Utils/UIDelegate.h"
"include/Utils/Utils.h"
"include/Utils/WebBrowserEventHandler.h"
"include/Utils/WinImplBase.h"
"include/Utils/WndShadow.h"
"include/Stdafx.h"
"include/UIlib.h"
"src/Control/UIActiveX.cpp"
"src/Control/UIButton.cpp"
"src/Control/UICheckBox.cpp"
"src/Control/UICombo.cpp"
"src/Control/UIDateTime.cpp"
"src/Control/UIEdit.cpp"
"src/Control/UIGifAnim.cpp"
"src/Control/UILabel.cpp"
"src/Control/UIList.cpp"
"src/Control/UIOption.cpp"
"src/Control/UIProgress.cpp"
"src/Control/UIRichEdit.cpp"
"src/Control/UIScrollBar.cpp"
"src/Control/UISlider.cpp"
"src/Control/UIText.cpp"
"src/Control/UITreeView.cpp"
"src/Control/UIWebBrowser.cpp"
"src/Core/UIBase.cpp"
"src/Core/UIContainer.cpp"
"src/Core/UIControl.cpp"
"src/Core/UIDlgBuilder.cpp"
"src/Core/UIManager.cpp"
"src/Core/UIMarkup.cpp"
"src/Core/UIRender.cpp"
"src/Layout/UIChildLayout.cpp"
"src/Layout/UIHorizontalLayout.cpp"
"src/Layout/UITabLayout.cpp"
"src/Layout/UITileLayout.cpp"
"src/Layout/UIVerticalLayout.cpp"
"src/Utils/stb_image.c"
"src/Utils/UIDelegate.cpp"
"src/Utils/Utils.cpp"
"src/Utils/WinImplBase.cpp"
"src/Utils/WndShadow.cpp"
"src/Utils/XUnzip.cpp"
"src/StdAfx.cpp"
"src/UIlib.cpp"
)
# dll
#add_definitions(-DUILIB_EXPORTS)
#add_library(duilib SHARED ${duilib_sources})

# lib
add_definitions(-DUILIB_STATIC)
add_library(duilib STATIC ${duilib_sources})


set(total_sources
${duilib_sources}
)
foreach(source IN LISTS total_sources)
    get_filename_component(source_path "${source}" PATH)
    string(REPLACE "/" "\\" source_path_msvc "${source_path}")
    source_group("${source_path_msvc}" FILES "${source}")
endforeach()












