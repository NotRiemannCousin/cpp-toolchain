cmake_minimum_required(VERSION 3.29)
project(cpp_toolchain_warmup LANGUAGES NONE)

include(${CMAKE_CURRENT_SOURCE_DIR}/get_cpm.cmake)

CPMAddPackage(
    NAME stdexec
    VERSION 0.10.0
    GITHUB_REPOSITORY NVIDIA/stdexec
    GIT_TAG nvhpc-26.05
    DOWNLOAD_ONLY YES
)

CPMAddPackage(
    NAME googletest
    GITHUB_REPOSITORY google/googletest
    GIT_TAG v1.15.2
    DOWNLOAD_ONLY YES
)

CPMAddPackage(
    NAME zlib
    GITHUB_REPOSITORY madler/zlib
    GIT_TAG v1.3.1
    DOWNLOAD_ONLY YES
)
