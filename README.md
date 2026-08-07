# 👋 Hi, I'm Prabhav Kasibhatla

🎓 **BS Computer Science & Computational Physics @ UT Austin**

I build systems at the intersection of low-level performance, machine learning, and computational physics.

### 🚀 Featured Projects

*   ⚛️ **[qmc-pricer](https://github.com/saiKasi0/qmc-pricer)**
    Quantum Amplitude Estimation for derivative pricing, built from scratch — including the simulator — and benchmarked against classical Monte Carlo **and** quasi-Monte Carlo.
    *   **The quadratic speedup is real, and it is not enough.** IQAE converges at `N^-1.01` against Monte Carlo's `N^-0.54` with non-overlapping confidence intervals — exactly what the literature promises. Scrambled-Sobol quasi-Monte Carlo reaches the *same rate* classically and beats every quantum method by **two orders of magnitude** in absolute error at every budget tested.
    *   **The simulator is mine.** A from-scratch statevector engine in Rust — memory-bandwidth-aware kernels, gate fusion, `rayon` — hitting **94% of this machine's measured 270 GB/s sustained bandwidth** at 26 qubits, slightly faster than Qiskit Aer. The denominator is benchmarked, not a spec sheet.
    *   **Two independent backends.** A Rust engine (hand-written index arithmetic over a flat buffer) and a JAX engine (tensor contractions) sharing no code, agreeing with each other and Qiskit to **4e-16**. A bug would have to be reproduced independently, in two languages, by two different algorithms, to survive.
    *   **What it would actually cost:** ~**9.2e12 T gates** and 61 logical qubits to price one option to 1e-4 — and the polynomial state preparation that would close that gap is precisely what Herbert's critique targets.

*   🔬 **[Preimage](https://github.com/saiKasi0/Preimage)**
    Amortized prompt inversion, evaluated *functionally*. Train a model that reads arbitrary text and emits a prompt making a frozen target model reproduce that text's **distribution** — judged by whether the regeneration matches, not by string-matching a "true" prompt (which, for arbitrary text, doesn't exist). At its core: the inverse problem for a stochastic simulator, i.e. amortized Bayesian inference.
    *   **Amortization beats search:** the reward-optimized inverter reaches **93% of best-of-8 search quality in a single call** (0.681 vs 0.732 embedding similarity) — above a 0.637 zero-shot bar and a 0.359 retrieval floor.
    *   **Reward hacking, measured and priced out:** ~24% of sampled candidate prompts attempt verbatim-copy strategies, with functional score correlating **+0.56** with target overlap absent the guard. The n-gram guard acts as a Bayesian prior term.
    *   **Built so the numbers can't be artifacts:** template-family-disjoint holdouts, pre-split MinHash dedup, provenance-split memorization controls separating *reachability* from *recall*, and metric sanity gates validated before any training.
    *   **Status:** complete config-driven pipeline, 52 tests, validated end-to-end at dev tier (135M stand-in). Full-scale 8B runs are config changes pending GPU allocation.

*   🧠 **[Lohalloc](https://github.com/saiKasi0/Lohalloc)**
    An intelligent, machine-learning-driven memory allocator that bridges ML and low-level systems architecture. A UCB1 multi-armed bandit learns per-call-site allocation topology during training, then freezes into a CHD minimal perfect hash table for O(1) routing at inference.
    *   **A specialist, honestly priced:** wins mixed-size/lifetime workloads by up to **6× on speed** and **4–16× on peak RSS** — and loses uniform small-object churn by 1.5–1.8×. Certified on bare-metal AWS Graviton across C/C++/Rust with Mann–Whitney U significance testing over raw per-run samples.
    *   **The bug worth reading about:** the bandit kept under-selecting the bump arena. The cause wasn't the allocator — a 48-byte training header was landing on the arena's cold target cache line, paying exactly the cache-miss cost the arena existed to avoid. The reward signal was measuring the instrument, not the system.
    *   **Live Telemetry Dashboard:** a custom real-time GUI (LOHA // ALLOC) monitoring heap maps, fragmentation, ops/sec, and latency — zero-overhead in production builds (feature-gated; verified via `nm`).

*   🎛️ **[CRATEDIG](https://github.com/saiKasi0/cratedig)**
    A real-time terminal sampler and sequencer in C++20, built because sample-based workflows are the one thing GarageBand handles poorly and the free alternatives are paywalled.
    *   **Hard real-time, enforced rather than intended:** zero allocations, locks, syscalls, or exceptions in the audio callback — three lanes over lock-free SPSC rings with a janitor thread that owns all destruction, checked by global `operator new` replacement against a thread-local depth counter and a ThreadSanitizer-clean suite.
    *   **Bit-exact determinism:** identical output across block sizes, run-to-run, and live-vs-offline, verified by committed golden hashes with a documented FMA-portability policy. Playback position is 32.32 fixed point, not float, so block-size invariance holds by construction rather than by luck.
    *   **Negative-control testing:** every assertion is validated by deliberately breaking the behavior it claims to catch. It found a full suite that passed with bus routing deleted entirely.
    *   **Status:** M5.7 of a documented 9-milestone roadmap. Chops, sequences, mixes. Not yet: recording, export, plugin hosting.

*   🦀 **[Iron Clad](https://github.com/saiKasi0/iron_clad)**
    A high-performance Unix shell in Rust, built to find out how much of a shell's latency is the shell's own fault. Unified my interests in core systems engineering (architecting the shell itself) and cloud infrastructure (AWS for rigorous benchmarking and validation).
    *   **Performance, on parity-verified workloads:** geometric mean **1.21×** over 15 cases vs `bash` — **1.84×** REPL dispatch (45.6% lower latency), **1.27×** spawn-and-reap at 250 concurrent jobs (21.2%), **1.24×** pipeline at 16 stages (19.4%), **1.14×** cold start (12.1%). Via `posix_spawn`-only execution (zero `fork()` calls, no CoW page-table cost), zero-copy fd passing (`libc::dup2`), and a borrowing parser over a recycled input buffer — 3 heap allocations for a simple command, pinned by a counting-allocator test.
    *   **Where it doesn't win, stated:** parse complexity 3 sits at **0.99×**, still a hair behind `bash`. Two parse cases were worse — 0.80×/0.83×, from spawning `/bin/echo` on every `echo` — until an `echo` builtin moved them to 1.15× and 0.99×.
    *   **Measured properly:** every benchmark pair is gated on a semantic parity check (stdout, exit status, and failure diagnostics must agree before timing), since Iron Clad implements a POSIX subset and an unsupported-syntax case would otherwise time `bash` doing work it skips. hyperfine `-N` at p50/p90/p99 on AWS Graviton bare metal via a zero-touch Terraform + Packer pipeline with automated `isolcpus` core isolation. Cold start n=100; other cases n=10, so p50 is the reportable statistic.

### 📂 Also

*   📦 **[WarrenDB](https://github.com/saiKasi0/WarrenDB)** — a distributed, erasure-coded, self-healing object store in Go, built as a controlled experiment in how storage systems should spend their repair I/O. ~1,200 seeded runs show corruption-aware scrub scheduling cuts unrecoverable data loss **54%** at equal I/O budget, and a deterministic harness collapses 30 days of cluster failure into a **14-second bit-for-bit reproducible run** over the real production code path.
*   📈 **[Proper Time](https://github.com/saiKasi0/proper_time)** — reproducing stochastic subordination (Clark 1973; Ané–Geman 2000) on 32M BTCUSDT tick trades: excess kurtosis collapses **~32 → ~2** moving from calendar to event time, with two *negative* results reported alongside it and an original `dτ/dt` "clock-rate" chart showing information intensity spiking ~100× around scheduled shocks.

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
