cmake_minimum_required(VERSION 3.5.0)

set(SOURCES main.cpp)
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

#set(CMAKE_CXX_FLAGS "-pthread") # для Linux
set(Boost_INCLUDE_DIR "/usr/local/boost_1_77_0")
set(Boost_LYBRARY_DIR "/usr/local/boost_1_77_0/stage/lib")

#set(Boost_USE_STATIC_LIBS        ON)  # only find static libs
#set(Boost_USE_DEBUG_LIBS        OFF)  # ignore debug libs and
#set(Boost_USE_RELEASE_LIBS       ON)  # only find release libs
#set(Boost_USE_MULTITHREADED      ON)
#set(Boost_USE_STATIC_RUNTIME    OFF)

find_package(Threads REQUIRED)
find_package(Boost COMPONENTS REQUIRED)


if(Boost_FOUND)
    
    include_directories(${Boost_INCLUDE_DIR})
    link_directories(${Boost_LYBRARY_DIR})

    add_executable(testBoost ${SOURCES})

    target_link_libraries(testBoost PRIVATE Threads::Threads)
    target_link_libraries(testBoost ${Boost_LYBRARIES})
    target_include_directories(testBoost PUBLIC ${MY_INCLUDE_DIR})

endif()

if(MINGW)
    target_link_libraries(testBoost ws2_32)
endif()