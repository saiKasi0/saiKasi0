# 👋 Hi, I'm Prabhav Kasibhatla

🎓 **BS Computer Science & Computational Physics @ UT Austin**

I'm a developer passionate about low-level systems programming, distributed systems, cloud, and ML.

### 🚀 Featured Projects

*   🔬 **[Preimage](https://github.com/saiKasi0/Preimage)**
    Amortized prompt inversion, evaluated *functionally*. Train a model that reads arbitrary text and emits a prompt making a frozen target model reproduce that text's **distribution** — judged by whether the regeneration matches, not by string-matching a "true" prompt (which, for arbitrary text, doesn't exist). At its core: the inverse problem for a stochastic simulator, i.e. amortized Bayesian inference.
    *   **Amortization beats search:** the reward-optimized inverter reaches **93% of best-of-8 search quality in a single call** (0.681 vs 0.732 embedding similarity) — above a 0.637 zero-shot bar and a 0.359 retrieval floor.
    *   **Reward hacking, measured and priced out:** ~24% of sampled candidate prompts attempt verbatim-copy strategies, with functional score correlating **+0.56** with target overlap absent the guard. The n-gram guard acts as a Bayesian prior term.
    *   **Built so the numbers can't be artifacts:** template-family-disjoint holdouts, pre-split MinHash dedup, provenance-split memorization controls separating *reachability* from *recall*, and metric sanity gates validated before any training.
    *   **Status:** complete config-driven pipeline, 52 tests, validated end-to-end at dev tier (135M stand-in). Full-scale 8B runs are config changes pending GPU allocation.

*   🧠 **[Lohalloc](https://github.com/saiKasi0/Lohalloc)**
    An intelligent, machine-learning-driven memory allocator that bridges ML and low-level systems architecture. A UCB1 multi-armed bandit learns per-call-site allocation topology during training, then freezes into a CHD minimal perfect hash table for O(1) routing at inference.
    *   **A specialist, honestly priced:** wins mixed-size/lifetime workloads by up to **6× on speed** and **4–16× on peak RSS** — and loses uniform small-object churn by 1.5–1.8×. Certified on bare-metal AWS Graviton across C/C++/Rust with Mann–Whitney U significance testing over raw per-run samples.
    *   **Live Telemetry Dashboard:** a custom real-time GUI (LOHA // ALLOC) monitoring heap maps, fragmentation, ops/sec, and latency — zero-overhead in production builds (feature-gated; verified via `nm`).
    *   **Adaptive Topologies:** distinct training and inference modes that analyze workload traces to converge on the most stable and performant memory layouts.

*   📦 **[WarrenDB](https://github.com/saiKasi0/WarrenDB)**
    A distributed, erasure-coded, self-healing object store in Go — built as a controlled experiment in how storage systems should spend their repair I/O. RS(k,m) erasure coding, BLAKE3/Merkle integrity, and an S3-compatible gateway.
    *   **A real experiment, not just a system:** ~1,200 seeded benchmark runs prove a corruption-aware scrub scheduler cuts unrecoverable data loss **54%** at equal I/O budget — worth a 2× scrub budget for free.
    *   **Deterministic simulation:** 30 days of cluster failure collapse into a **14-second, bit-for-bit reproducible** run, wrapping the real production node code so every simulated repair is the production path.

*   📈 **[Proper Time](https://github.com/saiKasi0/proper_time)**
    A market-microstructure study reproducing stochastic subordination (Clark 1973; Ané–Geman 2000) on 32M cleaned BTCUSDT tick trades — sampling price in *event time* (a clock that ticks with information arrival) instead of calendar time to recover the near-Gaussian process underneath.
    *   **The reproduction:** excess kurtosis collapses **~32 → ~2** moving from calendar to event-time bars; QQ tails straighten and Jarque–Bera falls ~175×.
    *   **Honest science:** reports two *negative* results too — event time redistributes rather than removes volatility clustering, and loses to calendar on out-of-sample vol forecasting. Clean results, reported as-is.
    *   **Original contribution:** a `dτ/dt` "clock-rate" chart showing information intensity spiking ~100× around scheduled shocks (CPI, FOMC, the ETF-approval news), then relaxing.

*   🦀 **[Iron Clad](https://github.com/saiKasi0/iron_clad)**
    A high-performance Unix shell in Rust, built to find out how much of a shell's latency is the shell's own fault. Unified my interests in core systems engineering (architecting the shell itself) and cloud infrastructure (AWS for rigorous benchmarking and validation).
    *   **Performance, parity-verified:** geometric mean **1.21×** over 15 cases vs `bash` on isolated-core Graviton bare metal — **1.84×** REPL dispatch (1000 iterations), **1.27×** spawn-and-reap (250 jobs), **1.24×** pipeline (16 stages), **1.14×** cold start (n=100). Via `posix_spawn`-only execution (zero `fork()` calls, no CoW page-table cost), zero-copy fd passing (`libc::dup2`), and a borrowing parser over a recycled input buffer.
    *   **Losses reported, not dropped:** parse complexity 3 sits at **0.99×**, still a hair behind `bash`. Two parse cases were worse — 0.80×/0.83×, from spawning `/bin/echo` on every `echo`; an `echo` builtin moved them to 1.15× and 0.99×.
    *   **Measured properly:** hyperfine `-N` (no intermediate shell) on AWS Graviton bare metal via a zero-touch Terraform + Packer pipeline with automated `isolcpus` core isolation. Cold start n=100; other cases n=10, so p50 is the reportable statistic and p90/p99 are spread, not tail estimates.

*   🖥️ **GPU Kernels** *(in progress — expected end of Fall 2026)*
    Climbing the SGEMM optimization ladder from a naive kernel to near-cuBLAS, with each rung explained by a profiler counter, then a fused capstone kernel.

### 🌱 What I'm Exploring

*   **Core Interests:** Systems, Machine Learning, Mathematics, Quant Research, and Quantum Computing.
*   **Currently Learning:** Compilers, GPU Software, Distributed Systems, Networking, and Market Microstructure.

### ⚡ Quick Facts

*   **Pronouns:** he/him
*   **Fun Fact:** I like coffee, basketball, and weightlifting

<!---
saiKasi0/saiKasi0 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
