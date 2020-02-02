################# dependencies #################
### Qt/KDE
find_package(Qt5 REQUIRED CONFIG COMPONENTS Widgets)

################# breezestyle target #################
set(breezecommon_LIB_SRCS
    breezeboxshadowrenderer.cpp
)

add_library(breezecommon5-scalable ${breezecommon_LIB_SRCS})

generate_export_header(breezecommon5-scalable
    BASE_NAME breezecommon
    EXPORT_FILE_NAME breezecommon_export.h)

target_link_libraries(breezecommon5-scalable
    PUBLIC
        Qt5::Core
        Qt5::Gui)

set_target_properties(breezecommon5-scalable PROPERTIES
    VERSION ${PROJECT_VERSION}
    SOVERSION ${PROJECT_VERSION_MAJOR})

install(TARGETS breezecommon5-scalable ${INSTALL_TARGETS_DEFAULT_ARGS} LIBRARY NAMELINK_SKIP)
