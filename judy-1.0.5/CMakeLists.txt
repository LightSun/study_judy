cmake_minimum_required(VERSION 3.5)

project(study_judy LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
SET(CMAKE_CXX_FLAGS "$CMAKE_CXX_FLAGS -fPIC")
SET(CMAKE_C_FLAGS "$CMAKE_C_FLAGS -fPIC")


##
add_compile_definitions(
    JUDYNEXT JUDYPREV
    JUDYGETINLINE
    NOSMARTJBB
    NOSMARTJBU
    NOSMARTJLB
    JU_64BIT
    )
include_directories(./)
include_directories(src/JudyCommon/)
include_directories(src/)
include_directories(src/JudyHS)
include_directories(src/JudySL)

#file(GLOB_RECURSE SRC_COMMON
#    src/JudyCommon/*.c src/JudyCommon/*.h)
set(SRC_COMMON
    src/JudyCommon/JudyByCount.c
    src/JudyCommon/JudyCascade.c
    src/JudyCommon/JudyCount.c
    src/JudyCommon/JudyCreateBranch.c
    src/JudyCommon/JudyDecascade.c
    src/JudyCommon/JudyDel.c
    src/JudyCommon/JudyFirst.c
    src/JudyCommon/JudyFreeArray.c
    src/JudyCommon/JudyGet.c
    src/JudyCommon/JudyInsArray.c
    src/JudyCommon/JudyIns.c
    src/JudyCommon/JudyInsertBranch.c
    src/JudyCommon/JudyMallocIF.c
    src/JudyCommon/JudyMemActive.c
    src/JudyCommon/JudyMemUsed.c
    src/JudyCommon/JudyPrevNext.c
    src/JudyCommon/JudyPrevNextEmpty.c
    src/JudyCommon/JudyTables.c
    )
#set_source_files_properties()

file(GLOB_RECURSE SRC_JUDY1
    src/Judy1/*.c src/Judy1/*.h)
file(GLOB_RECURSE SRC_JUDYL
    src/JudyL/*.c src/JudyL/*.h)
file(GLOB_RECURSE SRC_JUDYSL
    src/JudySL/*.c src/JudySL/*.h)
file(GLOB_RECURSE SRC_JUDYHS
    src/JudyHS/*.c src/JudyHS/*.h)

add_library(Judy1
    src/Judy.h
    #src/h7_config.h
    config.h
    ${SRC_COMMON}
   # ${SRC_JUDYL}
    ${SRC_JUDY1}
    ${SRC_JUDYSL}
    ${SRC_JUDYHS}
    )

target_compile_definitions(Judy1 PUBLIC JUDY1)
target_include_directories(Judy1 PUBLIC src/Judy1)

add_library(JudyL
    src/Judy.h
    config.h
    ${SRC_COMMON}
    ${SRC_JUDYL}
    ${SRC_JUDYSL}
    ${SRC_JUDYHS}
    )

target_compile_definitions(JudyL PUBLIC JUDYL)
target_include_directories(JudyL PUBLIC src/JudyL)
