cmake_minimum_required(VERSION 3.16)

project(WireScope VERSION 1.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

include_directories(${CMAKE_SOURCE_DIR}/include)

set(SOURCES
    # src/main.cpp
    src/main_dpi.cpp
    src/types.cpp
    src/pcap_reader.cpp
    src/packet_parser.cpp
    src/connection_tracker.cpp
    src/rule_manager.cpp
    src/sni_extractor.cpp
    src/fast_path.cpp
    src/load_balancer.cpp
    src/dpi_engine.cpp
)

add_executable(WireScope ${SOURCES})