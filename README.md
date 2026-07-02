# WireScope
<p align="center">

# 🚀 High-Performance Multi-Threaded Deep Packet Inspection (DPI) Engine

Modern C++17 • PCAP Processing • Connection Tracking • TLS SNI Extraction • Rule Engine

</p>

![C++](https://img.shields.io/badge/C%2B%2B-17-blue)
![CMake](https://img.shields.io/badge/CMake-3.16+-orange)
![Platform](https://img.shields.io/badge/Platform-Windows-success)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

---

# Overview

WireScope is a modular Deep Packet Inspection (DPI) engine written in modern C++.

The project demonstrates how enterprise DPI systems inspect network packets, classify traffic, maintain connection state, apply filtering rules and process packets concurrently using multiple worker threads.

Unlike a basic packet parser, WireScope implements a complete packet-processing pipeline with load balancing, fast-path processing, connection tracking and application classification.

---

# Features

- Offline PCAP processing
- Ethernet parsing
- IPv4 parsing
- TCP parsing
- UDP parsing
- TLS ClientHello detection
- Server Name Indication (SNI) extraction
- HTTP Host extraction
- DNS query extraction
- Five-Tuple flow identification
- Flow-aware load balancing
- Thread-safe queues
- Multi-threaded processing
- Connection tracking
- Rule based filtering
- Application classification
- Statistics collection
- PCAP output generation
- Modular C++ architecture

---

# Architecture

```text
               +------------------+
               |   PCAP Reader    |
               +--------+---------+
                        |
                        |
                  Five Tuple Hash
                        |
                        v
          +----------------------------+
          |       Load Balancer        |
          +-------------+--------------+
                        |
         +--------------+--------------+
         |              |              |
         v              v              v
      FastPath0     FastPath1     FastPathN
         |              |              |
         +--------------+--------------+
                        |
                  Output Queue
                        |
                        v
                  Output Writer
```

---

# Repository Structure

```text
WireScope/
│
├── include/
│   ├── types.h
│   ├── platform.h
│   ├── pcap_reader.h
│   ├── packet_parser.h
│   ├── thread_safe_queue.h
│   ├── connection_tracker.h
│   ├── rule_manager.h
│   ├── sni_extractor.h
│   ├── load_balancer.h
│   ├── fast_path.h
│   └── dpi_engine.h
│
├── src/
│   ├── main_dpi.cpp
│   ├── types.cpp
│   ├── pcap_reader.cpp
│   ├── packet_parser.cpp
│   ├── connection_tracker.cpp
│   ├── rule_manager.cpp
│   ├── sni_extractor.cpp
│   ├── load_balancer.cpp
│   ├── fast_path.cpp
│   └── dpi_engine.cpp
│
├── CMakeLists.txt
└── README.md
```

---

# Core Modules

## PCAP Reader
Reads offline packet captures, validates the PCAP header and streams packets into the processing pipeline.

## Packet Parser
Parses Ethernet, IPv4, TCP and UDP headers while exposing payload data for higher-level inspection.

## Connection Tracker
Maintains per-flow state using the five-tuple and records packets, bytes, timestamps and classification results.

## Rule Manager
Supports IP, application, domain and port based filtering.

## SNI Extractor
Extracts TLS Server Name Indication from ClientHello packets to identify encrypted applications.

## Load Balancer
Hashes each flow to ensure packets from the same connection always reach the same worker thread.

## Fast Path
Performs parsing, connection lookup, classification, rule evaluation and statistics updates.

## DPI Engine
Coordinates the reader thread, load balancers, fast-path workers and output writer.

---

# Packet Processing Pipeline

```text
Read Packet
      ↓
Parse Ethernet
      ↓
Parse IPv4
      ↓
Parse TCP/UDP
      ↓
Generate Five Tuple
      ↓
Load Balancer
      ↓
Fast Path Worker
      ↓
Connection Tracker
      ↓
SNI Extraction
      ↓
Application Classification
      ↓
Rule Evaluation
      ↓
Forward / Drop
      ↓
Write Output PCAP
```

---

# Technologies

- C++17
- STL
- Threads
- Mutex
- Shared Mutex
- Condition Variables
- Atomic Variables
- CMake
- Git
- GitHub

---

# Build

```bash
git clone https://github.com/Akriti339/WireScope.git
cd WireScope
mkdir build
cd build
cmake ..
cmake --build . --config Release
```

---

# Usage

```bash
WireScope input.pcap output.pcap
```

Block an application

```bash
WireScope input.pcap output.pcap --block-app YouTube
```

Block a domain

```bash
WireScope input.pcap output.pcap --block-domain *.facebook.com
```

Block an IP

```bash
WireScope input.pcap output.pcap --block-ip 192.168.1.10
```

---

# Current Status

| Feature | Status |
|---------|--------|
| PCAP Reader | ✅ |
| Packet Parser | ✅ |
| Connection Tracking | ✅ |
| Rule Engine | ✅ |
| SNI Extraction | ✅ |
| Load Balancer | ✅ |
| Fast Path | ✅ |
| DPI Engine | ✅ |
| Offline Processing | ✅ |
| Live Capture | 🚧 |

---

# Future Work

- IPv6 support
- QUIC / HTTP3 support
- Live packet capture
- REST API
- Web dashboard
- DPDK integration
- eBPF integration
- Performance benchmarking
- Unit tests
- CI/CD pipeline

---

<!-- # Screenshots

> Add screenshots of:
>
> - Console execution
> - Packet statistics
> - Architecture diagram
> - Example output

--- -->

# Author

**Akriti Gupta**

B.Tech, IIT (BHU) Varanasi

GitHub: https://github.com/Akriti339

---

# License

MIT License

Copyright (c) 2026 Akriti Gupta

<!-- 
## Appendix 1

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 1.


## Appendix 2

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 2.


## Appendix 3

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 3.


## Appendix 4

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 4.


## Appendix 5

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 5.


## Appendix 6

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 6.


## Appendix 7

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 7.


## Appendix 8

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 8.


## Appendix 9

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 9.


## Appendix 10

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 10.


## Appendix 11

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 11.


## Appendix 12

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 12.


## Appendix 13

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 13.


## Appendix 14

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 14.


## Appendix 15

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 15.


## Appendix 16

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 16.


## Appendix 17

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 17.


## Appendix 18

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 18.


## Appendix 19

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 19.


## Appendix 20

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 20.


## Appendix 21

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 21.


## Appendix 22

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 22.


## Appendix 23

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 23.


## Appendix 24

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 24.


## Appendix 25

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 25.


## Appendix 26

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 26.


## Appendix 27

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 27.


## Appendix 28

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 28.


## Appendix 29

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 29.


## Appendix 30

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 30.


## Appendix 31

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 31.


## Appendix 32

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 32.


## Appendix 33

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 33.


## Appendix 34

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 34.


## Appendix 35

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 35.


## Appendix 36

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 36.


## Appendix 37

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 37.


## Appendix 38

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 38.


## Appendix 39

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 39.


## Appendix 40

This section can document implementation details, benchmarks, protocol notes, design decisions, testing methodology, or future enhancements related to WireScope module 40. -->
