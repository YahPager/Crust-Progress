# Whole-process AOT/JIT comparison

October 28, 2026. Opt-in Windows x64 JIT execution and selected native interfaces are verified. AOT remains the default. All 180 compiler tests pass, including checked failures, all six C/C++/Rust call directions, cleanup, exceptions/panics and native-library lifecycle cases.

A later October 28 compiler change is recorded in the [progress journal](PROGRESS.md#october-28-2026---faster-jit-startup-and-a-faster-checked-sum). The tables below are the earlier campaigns and were not replaced.

Two complete campaigns each retained 250 process samples: two warmups and three measurements for every workload/size/mode and empty-startup case. Each campaign passed 30 independent small full-output controls; all timed application checksums passed. No timing sample was dropped.

The fresh local runs use Windows 11 build 26200 on an Intel Core Ultra 7 265K, with Clang/LLVM 22.1.6 and Rust 1.97.1. Optimized builds use baseline x86-64 and ordinary floating-point semantics. Safety checks and interface boundaries differ between languages.

## Best of three measured runs

Times are milliseconds from the second complete campaign. Allocation, input generation, computation, result output and cleanup are included. AOT times start with prebuilt executable launch; their builds are reported separately below. Crust JIT includes its complete source-to-run compilation and startup path.

The three Goose columns preserve the published October 16 values. Those were measured on a different Ryzen 9 9950X3D machine, with different allocation and compilation behavior. They are historical context, not a same-machine ranking.

| Case | Size | C | C++ | Rust | Crust AOT | Crust JIT | Goose AOT/MSVC | Goose AOT/clang | Goose JIT |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| sum | 1000000 | 15.086 | 15.834 | 16.593 | 16.566 | 710.461 | 16.3 | 16.0 | 42.5 |
| sum | 16000000 | 73.429 | 79.520 | 101.422 | 86.851 | 769.879 | 50.2 | 54.8 | 196.9 |
| sum | 128000000 | 473.086 | 554.735 | 685.507 | 589.957 | 1294.830 | 298.8 | 318.5 | 1333.8 |
| blur | 1024 | 20.119 | 20.320 | 21.012 | 20.496 | 742.714 | 32.4 | 19.5 | 189.6 |
| blur | 2048 | 45.046 | 45.410 | 46.010 | 45.220 | 764.050 | 76.3 | 29.8 | 649.8 |
| blur | 8192 | 525.748 | 542.969 | 540.146 | 530.237 | 1236.448 | 952.1 | 266.0 | 9917.6 |
| particles | 100000 | 28.319 | 30.688 | 30.916 | 27.525 | 774.173 | 29.6 | 29.4 | 95.3 |
| particles | 1000000 | 304.164 | 333.956 | 337.060 | 293.593 | 1008.490 | 170.3 | 162.9 | 679.1 |
| particles | 4000000 | 1475.952 | 1475.180 | 1578.527 | 1513.220 | 2194.775 | 856.1 | 831.2 | 2573.4 |


Crust JIT is slower than every fresh local AOT mode in these runs. Small cases are dominated by its compilation and startup costs. AOT results vary by workload; the large sum remains slower than C. The different historical Goose machine and boundaries prevent attributing these differences to the languages alone.

## Repeatability at the largest sizes

Median and observed range in milliseconds; each cell contains three measurements. All observations are retained, including the substantial variation between campaigns.

| Case | Crust AOT, campaign 1 | Crust AOT, campaign 2 | Crust JIT, campaign 1 | Crust JIT, campaign 2 |
|---|---|---|---|---|
| sum | 672.878 (666.249-681.998) | 606.329 (589.957-608.858) | 1411.656 (1367.932-1419.869) | 1297.107 (1294.830-1315.911) |
| blur | 538.106 (531.400-544.518) | 530.273 (530.237-530.981) | 1287.076 (1254.825-1308.811) | 1240.989 (1236.448-1278.503) |
| particles | 1661.889 (1600.392-1676.532) | 1525.353 (1513.220-1620.596) | 2404.083 (2315.288-2414.528) | 2221.599 (2194.775-2266.689) |


## Empty application startup

Best of three measured runs, after two warmups, in milliseconds:

| Mode | Campaign 1 | Campaign 2 |
|---|---:|---:|
| c | 12.854 | 12.637 |
| cpp | 12.171 | 13.017 |
| rust | 12.072 | 13.065 |
| crust-aot | 11.839 | 12.663 |
| crust-jit | 279.703 | 285.574 |


Goose published empty-program floors of 13.1 ms AOT and 30.5 ms JIT, using best of five runs on its different machine.

## Memory boundaries

Maximum process peaks across the second campaign measured runs, in MiB. Each JIT column describes a separate process; the peaks must not be added as a simultaneous process-tree peak. The compiler column is the largest individual compiler process.

| Largest case | C | C++ | Rust | Crust AOT | JIT driver | JIT worker | JIT compiler |
|---|---:|---:|---:|---:|---:|---:|---:|
| sum | 491.98 | 491.99 | 492.05 | 492.00 | 6.67 | 512.27 | 42.77 |
| blur | 131.70 | 131.71 | 131.77 | 131.72 | 6.64 | 155.94 | 42.84 |
| particles | 95.25 | 95.26 | 95.32 | 95.27 | 6.74 | 117.21 | 42.77 |


The compiled local cases use exact-size initialized storage. Goose uses grow-only storage; its historical large-case AOT/JIT peaks, labeled MB in the original report, are 496.1/499.4 for sum, 135.8/139.2 for blur and 99.3/103.2 for particles. Its JIT peak covers a different process boundary. These results establish no allocator or general memory advantage.

## AOT build costs

Build wall time in milliseconds: median and range across the nine published-size builds in each campaign, one build per case. These are separate from the application times above. JIT compilation is already included in its application latency.

| Mode | Campaign 1 | Campaign 2 |
|---|---|---|
| c | 137.296 (125.920-157.018) | 132.774 (125.244-140.902) |
| cpp | 396.241 (369.678-410.948) | 383.677 (366.194-394.287) |
| rust | 202.370 (189.112-234.216) | 193.618 (188.948-215.899) |
| crust-aot | 715.864 (674.663-778.995) | 696.574 (682.260-730.385) |


## Scope and attribution

The selected workloads are sum at 1/16/128 million elements, flat blur at widths 1024/2048/8192, and scalar f32 particles at 0.1/1/4 million particles. The full published suite, alternate variants, additional platforms and clean-environment packaging remain unverified. Three measurements per cell do not establish statistical superiority or an overall language ranking.

Historical figures and workload definitions: [Goose benchmark report, pinned October 16 snapshot](https://github.com/aardappel/goose/blob/cce94b919d27458856ae2685974049eac78debcf/bench/results.md#goose-compiled-vs-jit). Goose was not executed for this comparison.

[Project introduction](README.md) | [Progress journal](PROGRESS.md)
