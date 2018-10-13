cmake_minimum_required(VERSION 3.0.0)
project(do_forest VERSION 0.1.0)
set (CMAKE_CXX_STANDARD 11)
include(CTest)
enable_testing()

ADD_CUSTOM_COMMAND( OUTPUT tree_reflection.h tree_apply.h tree_types.h
                    COMMAND gbc c++ tree.bond
                    DEPENDS tree.bond
                    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
                    COMMENT "generating bond code" )

add_executable(do_forest do_forest.cpp tree_reflection.h)



set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
