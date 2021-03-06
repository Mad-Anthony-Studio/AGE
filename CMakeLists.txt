cmake_minimum_required(VERSION 2.6)

project(AdvancedGenieEditor3)

set(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake/)
set(ICONV_LIBRARIES "C:/Cpp/MinGW/lib/libiconv.a")
set(CMAKE_CXX_FLAGS "-std=gnu++0x")
set(Boost_USE_STATIC_LIBS    ON)
set(Boost_USE_MULTITHREADED  ON)
set(Boost_USE_STATIC_RUNTIME ON)

find_package(Boost 1.42 COMPONENTS iostreams REQUIRED)
find_package(wxWidgets COMPONENTS adv core base REQUIRED)
#find_package(SFML 1.6 graphics REQUIRED)

include("${wxWidgets_USE_FILE}")

set(GDAT_TOOLS FALSE)
set(GDAT_STATIC TRUE)
set(GUTILS_TOOLS FALSE)
set(GUTILS_TEST FALSE)

include_directories(
    ${CMAKE_HOME_DIRECTORY}/extern/genieutils/include 
	${Boost_INCLUDE_DIRS})

add_subdirectory(extern/genieutils)

set(AGE_SRC Main.cpp
			AGE_TextControls.cpp
			AGE_CheckBoxes.cpp
			AGE_ComboBoxes.cpp
			AGE_AboutDialog.cpp
			AGE_OpenDialog.cpp
			AGE_SaveDialog.cpp

			AGE_Frame/Constructor.cpp
			AGE_Frame/Other.cpp
			#AGE_Frame/DRS.cpp
			AGE_Frame/Civs.cpp
			AGE_Frame/General.cpp
			AGE_Frame/Graphics.cpp
			AGE_Frame/PlayerColors.cpp
			AGE_Frame/Research.cpp
			AGE_Frame/Sounds.cpp
			AGE_Frame/Techs.cpp
			AGE_Frame/TechTrees.cpp
			AGE_Frame/TerrainBorders.cpp
			AGE_Frame/TerrainRestrictions.cpp
			AGE_Frame/Terrains.cpp
			AGE_Frame/UnitLine.cpp
			AGE_Frame/Units.cpp
			#AGE_Frame/Transporting.cpp

			Resources.rc
	)

add_executable(AdvancedGenieEditor3 WIN32 ${AGE_SRC})

target_link_libraries(AdvancedGenieEditor3 ${wxWidgets_LIBRARIES} genieutils)
