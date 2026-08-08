# AXI4 High-Performance Memory Slave (Microarchitecture)

This repository details the microarchitecture for a full AXI4 memory slave designed to eliminate blocking bottlenecks. The architecture focuses on high-throughput data routing, deterministic execution, and strict AMBA protocol compliance.

**Key Architectural Features:**
* **Out-of-Order Execution & INCR Bursts:** Supports high-performance execution capabilities to maximize bus utilization.
* **Decoupled Channels & Token Synchronization:** Integrates pipelined skid buffers at the bus interfaces with completely decoupled address (AW) and data (W) channels, utilizing Token FIFOs to strictly synchronize data beats with their corresponding addresses.
* **Cross-Group Hazard Scoreboard:** Employs parallel, per-ID pending FIFOs integrated with a combinatorial scoreboard utilizing up/down counters. This physically prevents structural hazards and guarantees in-order completion for identical IDs.
* **Asymmetric Interleaved Memory:** Implements round-robin arbiters to dynamically distribute unstalled requests from the per-ID FIFOs across two interleaved execution groups with asymmetric access latencies (2-cycle and 4-cycle).

## Project Status
**Phase:** Microarchitecture & Documentation 
*RTL Design and Verification are currently ongoing.* 

This repository currently hosts the system-level architectural specifications, data path logic, and stall/release mechanisms.

## References
* **AMBA AXI and ACE Protocol Specification:** All architectural decisions, ordering models, and protocol compliance mechanisms detailed in this project were designed in accordance with the official ARM specification document: [`IHI0022E_amba_axi_and_ace_protocol_spec.pdf`](https://support.arm.com/documentation/ihi0022/e/).

## File Structure
```text
├── docs/
│   ├── AXI4_Mem_Slave_Architecture.pdf      # Detailed microarchitecture specification and protocol compliance
│   └── AXI4_MEM_SLAVE_ARCH.jpg              # High-level block diagram of the Write and Read paths
└── README.md
```

Copyright (C) 2026 Anish Dey. All rights reserved.