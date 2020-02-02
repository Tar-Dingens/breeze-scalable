project(breeze)
set(PROJECT_VERSION "5.17.90")
set(PROJECT_VERSION_MAJOR 5)

cmake_minimum_required(VERSION 2.8.12 FATAL_ERROR)

include(GenerateExportHeader)
include(WriteBasicConfigVersionFile)
include(FeatureSummary)

find_package(ECM 0.0.9 REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${ECM_MODULE_PATH} ${ECM_KDE_MODULE_DIR} ${CMAKE_SOURCE_DIR}/cmake)

include(ECMInstallIcons)
include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings NO_POLICY_SCOPE)
include(KDEClangFormat)

include(GtkUpdateIconCache)

add_subdirectory(libbreezecommon)
add_subdirectory(kstyle)

find_package(KF5Package CONFIG REQUIRED)
if(EXISTS ${CMAKE_SOURCE_DIR}/po AND IS_DIRECTORY ${CMAKE_SOURCE_DIR}/po)
    find_package(KF5I18n CONFIG REQUIRED)
    ki18n_install(po)
endif()

feature_summary(WHAT ALL INCLUDE_QUIET_PACKAGES FATAL_ON_MISSING_REQUIRED_PACKAGES)
