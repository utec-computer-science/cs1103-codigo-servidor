cmake_minimum_required(VERSION 3.12.3)
project(battleship_server)

project(battleship_server
	VERSION 0.0.0
	DESCRIPTION "Battleship server"
	HOMEPAGE_URL "https://github.com/utec-computer-science/cs1103-codigo-servidor"
	LANGUAGES "CXX"
)

include(GNUInstallDirs)
include(FindPkgConfig)
include(CPack)

set(CMAKE_CXX_STANDARD 17)
set( CMAKE_VERBOSE_MAKEFILE on)
if(WIN32)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall")
elseif(UNIX AND NOT APPLE)
    set(CMAKE_CXX_FLAGS -pthread)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wpedantic -Wextra")
else()
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wpedantic -Wextra")
endif()

add_executable(battleship_server main.cpp common_types.h player.cpp player.h controller.cpp controller.h)
if(UNIX AND NOT APPLE)
    target_link_libraries(battleship_server stdc++fs)
endif()

# Install target
install(TARGETS ${PROJECT_NAME}
	DESTINATION ${CMAKE_INSTALL_BINDIR}
)

# *.deb
configure_file(CPackConfig.cmake.in
	${CMAKE_BINARY_DIR}/CPackConfig.cmake
)
