cmake_minimum_required( VERSION 3.7 )
project( ibpp VERSION "0.0.1" )

set( CMAKE_CXX_STANDARD 11)
set( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -m64 -Wall -pedantic -Wextra -Wlogical-op -Wconversion -Wno-unused-parameter -Wsuggest-attribute=noreturn -Wsuggest-override -Wold-style-cast" )

set( CMAKE_CXX_FLAGS_RELEASE "-g0 -DNDEBUG -Ofast")
set( CMAKE_CXX_FLAGS_DEBUG "-g -DDEBUG -O")

if (WIN32)
    add_definitions( -DIBPP_WINDOWS )
endif (WIN32)

if (UNIX)
    add_definitions( -DIBPP_LINUX )
endif (UNIX)

if (MSVC)
    add_definitions( -DIBPP_WINDOWS )
endif (MSVC)

if( APPLE)
    add_definitions( -DIBPP_DARWIN )
endif (APPLE)


file( GLOB _SRC
    "source/*.cpp"
)

add_library( ${PROJECT_NAME} SHARED ${_SRC}) # STATIC

target_include_directories( ${PROJECT_NAME} PUBLIC include)

#target_link_libraries(${PROJECT_NAME} " ... deps none ... ")

set_target_properties( ${PROJECT_NAME} PROPERTIES
    SOVERSION ${PROJECT_VERSION_MAJOR}
    VERSION ${PROJECT_VERSION}
)

INSTALL( TARGETS ${PROJECT_NAME} DESTINATION /usr/lib/kansoftware)

INSTALL( DIRECTORY "${CMAKE_SOURCE_DIR}/include/"
    DESTINATION /usr/include/kansoftware
    FILES_MATCHING
    PATTERN "*.h"
)

set( CPACK_GENERATOR "DEB")
set( CPACK_PACKAGE_VERSION_MAJOR ${PROJECT_VERSION_MAJOR})
set( CPACK_PACKAGE_VERSION_MINOR ${PROJECT_VERSION_MINOR})
set( CPACK_PACKAGE_VERSION_PATCH ${PROJECT_VERSION_PATCH})
#set( CPACK_DEBIAN_PACKAGE_DEPENDS " ... deps none ... ")
set( CPACK_PACKAGE_DESCRIPTION "IBPP, where the 'PP' stands for '++', is a C ++ client interface for Firebird SQL")
set( CPACK_PACKAGE_CONTACT "Andrew KAN kan@kansoftware.ru")
#set( CPACK_DEBIAN_PACKAGE_CONTROL_EXTRA "${CMAKE_CURRENT_SOURCE_DIR}/Debian/postinst")

include( CPack)
