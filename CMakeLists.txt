# This file is part of Telegram Desktop,
# the official desktop application for the Telegram messaging service.
#
# For license and copyright information please follow this link:
# https://github.com/telegramdesktop/tdesktop/blob/master/LEGAL

cmake_minimum_required(VERSION 3.16)
cmake_policy(SET CMP0076 NEW)
cmake_policy(SET CMP0091 NEW)

set_property(GLOBAL PROPERTY USE_FOLDERS ON)

include(cmake/validate_special_target.cmake)
include(cmake/version.cmake)
desktop_app_parse_version(Telegram/build/version)

project(NebulaChat
    LANGUAGES C CXX
    VERSION ${desktop_app_version_cmake}
    DESCRIPTION "Official NebulaChat Desktop messenger"
    HOMEPAGE_URL "https://nebula.chat"
)
set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT NebulaChat)

include(cmake/variables.cmake)
include(cmake/nice_target_sources.cmake)
include(cmake/target_link_static_libraries.cmake)
include(cmake/target_link_frameworks.cmake)
include(cmake/init_target.cmake)
include(cmake/generate_target.cmake)

include(cmake/options.cmake)

include(cmake/external/qt/package.cmake)

add_subdirectory(cmake)
add_subdirectory(Telegram)
