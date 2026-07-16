# 👋 Hi, I’m Prabhav Kasibhatla

🎓 **BS Computer Science & Computational Physics @ UT Austin**

I'm a developer passionate about low-level systems programming, distributed systems, cloud, and ML.

### 🚀 Featured Projects

*   🦀 **[Iron Clad](https://github.com/saiKasi0/iron_clad)** 
    A high-performance shell written in Rust. Building this unified my interests in core systems engineering (architecting the shell itself) and cloud infrastructure (leveraging AWS for rigorous benchmarking and validation).
    *   **Performance:** Achieved up to a **x94 speedup** on specific parallel tasks.
    *   **Memory Efficiency:** Delivered an **order of magnitude improvement** in memory spawn speedups compared to standard environments, with consistent, within-magnitude speedups across all other operations.

*   🧠 **[Lohalloc](https://github.com/saiKasi0/Lohalloc)**
    An intelligent, machine-learning-driven memory allocator that bridges ML and low-level systems architecture. It dynamically learns and adapts allocation strategies to minimize fragmentation and optimize throughput.
    *   **Live Telemetry Dashboard:** Includes a custom real-time GUI (LOHA // ALLOC) to monitor heap maps, memory fragmentation percentages, operations per second, and latency.
    *   **Adaptive Topologies:** Features distinct "training" and "inference" modes that analyze workload traces to converge on the most stable and performant memory layouts.

*   📦 **[WarrenDB](https://github.com/saiKasi0/WarrenDB)**
    A distributed, erasure-coded, self-healing object store in Go — built as a controlled experiment in how storage systems should spend their repair I/O. RS(k,m) erasure coding, BLAKE3/Merkle integrity, and an S3-compatible gateway.
    *   **A real experiment, not just a system:** ~1,200 seeded benchmark runs prove a corruption-aware scrub scheduler cuts unrecoverable data loss **54%** at equal I/O budget — worth a 2× scrub budget for free.
    *   **Deterministic simulation:** 30 days of cluster failure collapse into a **14-second, bit-for-bit reproducible** run, wrapping the real production node code so every simulated repair is the production path.

*   📈 **[Proper Time](https://github.com/saiKasi0/proper_time)**
    A market-microstructure study reproducing stochastic subordination (Clark 1973; Ané–Geman 2000) on 32M cleaned BTCUSDT tick trades — sampling price in *event time* (a clock that ticks with information arrival) instead of calendar time to recover the near-Gaussian process underneath.
    *   **The reproduction:** excess kurtosis collapses **~32 → ~2** moving from calendar to event-time bars; QQ tails straighten and Jarque–Bera falls ~175×.
    *   **Honest science:** reports two *negative* results too — event time redistributes rather than removes volatility clustering, and loses to calendar on out-of-sample vol forecasting. Clean results, reported as-is.
    *   **Original contribution:** a `dτ/dt` "clock-rate" chart showing information intensity spiking ~100× around scheduled shocks (CPI, FOMC, the ETF-approval news), then relaxing.

### 🌱 What I'm Exploring

*   **Core Interests:** Systems, Machine Learning, Mathematics, Quant Research, and Quantum Computing.
*   **Currently Learning:** Distributed systems, networking, and market microstructure.

### ⚡ Quick Facts
*   **Pronouns:** he/him
*   **Fun Fact:** I like coffee, basketball, and weightlifting

<!---
saiKasi0/saiKasi0 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
