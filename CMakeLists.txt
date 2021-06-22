cmake_minimum_required(VERSION 3.11)
project(solar)

file(MAKE_DIRECTORY install)

include(ExternalProject)

ExternalProject_Add(proto
    GIT_REPOSITORY git@github.com:madmann91/proto
    INSTALL_COMMAND ""
    CMAKE_ARGS -DBUILD_TESTING=OFF -DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE})
ExternalProject_Get_Property(proto BINARY_DIR)
set(proto_BINARY_DIR ${BINARY_DIR})
ExternalProject_Add_StepDependencies(bvh configure proto)

ExternalProject_Add(bvh
    GIT_REPOSITORY git@github.com:madmann91/bvh
    GIT_TAG origin/v2
    INSTALL_COMMAND ""
    CMAKE_ARGS -Dproto_DIR=${proto_BINARY_DIR} -DBUILD_TESTING=OFF -DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE})
ExternalProject_Get_Property(bvh BINARY_DIR)
set(bvh_BINARY_DIR ${BINARY_DIR})
ExternalProject_Add_StepDependencies(bvh configure proto)

ExternalProject_Add(sol
    GIT_REPOSITORY git@github.com:madmann91/sol
    GIT_SUBMODULES_RECURSE FALSE
    INSTALL_COMMAND ""
    CMAKE_ARGS -Dproto_DIR=${proto_BINARY_DIR} -Dbvh_DIR=${bvh_BINARY_DIR} -DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE})
ExternalProject_Add_StepDependencies(sol configure proto bvh)
