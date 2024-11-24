cmake_minimum_required(VERSION 3.12)
project(xinput1_3)

set(CMAKE_CXX_STANDARD 17)
enable_language(ASM_MASM)
set(CMAKE_BUILD_TYPE Release)

include_directories("C:\\Program Files (x86)\\Microsoft Visual Studio\\2022\\BuildTools\\VC\\Tools\\MSVC\\14.34.31933\\atlmfc\\include")
include_directories("C:\\Program Files (x86)\\Microsoft Visual Studio\\2022\\BuildTools\\DIA SDK\\include")
include_directories("${PROJECT_SOURCE_DIR}/asmjit")
add_subdirectory(${CMAKE_CURRENT_LIST_DIR}/zydis "zydis" EXCLUDE_FROM_ALL)

file(GLOB source_list "src/*")
add_library(xinput1_3 SHARED ${source_list})
target_link_libraries(xinput1_3 "Zydis")
target_link_libraries(xinput1_3 "C:\\Program Files (x86)\\Microsoft Visual Studio\\2022\\BuildTools\\DIA SDK\\lib\\amd64\\diaguids.lib")
target_link_libraries(xinput1_3 "C:\\Program Files (x86)\\Microsoft Visual Studio\\2022\\BuildTools\\VC\\Tools\\MSVC\\14.34.31933\\atlmfc\\lib\\x64\\atls.lib")
target_link_libraries(xinput1_3 "${PROJECT_SOURCE_DIR}/lib/asmjit.lib")