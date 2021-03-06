```ini
BenchmarkDotNet=v0.12.0, OS=Windows 10.0.18363
Intel Xeon CPU E5-2678 v3 2.50GHz, 1 CPU, 24 logical and 12 physical cores
.NET Core SDK=3.1.100
  [Host]     : .NET Core 3.1.0 (CoreCLR 4.700.19.56402, CoreFX 4.700.19.56404), X64 RyuJIT
  Job-FBNCAJ : .NET Core 3.1.0 (CoreCLR 4.700.19.56402, CoreFX 4.700.19.56404), X64 RyuJIT

Runtime=.NET Core 3.1  
```

|         Method | Times |           Mean |         Error |        StdDev |  Ratio | RatioSD | Rank | Gen 0 | Gen 1 | Gen 2 | Allocated |
|--------------- |------ |---------------:|--------------:|--------------:|-------:|--------:|-----:|------:|------:|------:|----------:|
|       Directly |    10 |       3.359 ns |     0.0340 ns |     0.0302 ns |   1.00 |    0.00 |    1 |     - |     - |     - |         - |
|      TableFunc |    10 |     298.712 ns |     0.6967 ns |     0.6517 ns |  88.92 |    0.87 |    5 |     - |     - |     - |         - |
|     Reflection |    10 |     967.851 ns |     2.9807 ns |     2.7881 ns | 288.16 |    2.58 |    6 |     - |     - |     - |         - |
|           Func |    10 |      20.642 ns |     0.0488 ns |     0.0408 ns |   6.15 |    0.05 |    2 |     - |     - |     - |         - |
| ExpressionFunc |    10 |      42.828 ns |     0.7669 ns |     0.7173 ns |  12.74 |    0.22 |    3 |     - |     - |     - |         - |
|        Dynamic |    10 |      97.422 ns |     0.1291 ns |     0.1145 ns |  29.01 |    0.26 |    4 |     - |     - |     - |         - |
|                |       |                |               |               |        |         |      |       |       |       |           |
|       Directly |   100 |      41.599 ns |     0.0562 ns |     0.0439 ns |   1.00 |    0.00 |    1 |     - |     - |     - |         - |
|      TableFunc |   100 |   2,846.466 ns |     7.0717 ns |     6.6149 ns |  68.45 |    0.13 |    5 |     - |     - |     - |         - |
|     Reflection |   100 |   9,517.646 ns |    58.4239 ns |    54.6498 ns | 228.75 |    1.59 |    6 |     - |     - |     - |         - |
|           Func |   100 |     212.815 ns |     0.5178 ns |     0.4843 ns |   5.11 |    0.01 |    2 |     - |     - |     - |         - |
| ExpressionFunc |   100 |     418.458 ns |     0.7712 ns |     0.7214 ns |  10.06 |    0.02 |    3 |     - |     - |     - |         - |
|        Dynamic |   100 |     877.986 ns |     2.6677 ns |     2.4954 ns |  21.12 |    0.06 |    4 |     - |     - |     - |         - |
|                |       |                |               |               |        |         |      |       |       |       |           |
|       Directly |  1000 |     355.713 ns |     6.1893 ns |     5.7895 ns |   1.00 |    0.00 |    1 |     - |     - |     - |         - |
|      TableFunc |  1000 |  28,277.464 ns |    58.4593 ns |    54.6828 ns |  79.51 |    1.31 |    5 |     - |     - |     - |         - |
|     Reflection |  1000 |  94,468.767 ns |   332.5024 ns |   311.0230 ns | 265.65 |    4.89 |    6 |     - |     - |     - |         - |
|           Func |  1000 |   2,083.389 ns |     5.8047 ns |     5.4297 ns |   5.86 |    0.10 |    2 |     - |     - |     - |         - |
| ExpressionFunc |  1000 |   4,148.128 ns |    14.5502 ns |    13.6103 ns |  11.66 |    0.19 |    3 |     - |     - |     - |         - |
|        Dynamic |  1000 |   8,569.997 ns |    95.2861 ns |    89.1307 ns |  24.10 |    0.30 |    4 |     - |     - |     - |         - |
|                |       |                |               |               |        |         |      |       |       |       |           |
|       Directly |  5000 |   1,717.225 ns |     5.8801 ns |     5.5003 ns |   1.00 |    0.00 |    1 |     - |     - |     - |         - |
|      TableFunc |  5000 | 140,861.001 ns |   360.8811 ns |   337.5684 ns |  82.03 |    0.22 |    5 |     - |     - |     - |         - |
|     Reflection |  5000 | 469,242.100 ns | 1,175.0178 ns | 1,041.6226 ns | 273.36 |    0.96 |    6 |     - |     - |     - |       1 B |
|           Func |  5000 |  11,994.478 ns |    23.6693 ns |    22.1403 ns |   6.98 |    0.03 |    2 |     - |     - |     - |         - |
| ExpressionFunc |  5000 |  21,652.651 ns |   365.3636 ns |   341.7613 ns |  12.61 |    0.19 |    3 |     - |     - |     - |         - |
|        Dynamic |  5000 |  41,878.419 ns |   617.8915 ns |   577.9761 ns |  24.39 |    0.35 |    4 |     - |     - |     - |         - |
|                |       |                |               |               |        |         |      |       |       |       |           |
|       Directly | 10000 |   3,466.540 ns |    11.8589 ns |    11.0928 ns |   1.00 |    0.00 |    1 |     - |     - |     - |         - |
|      TableFunc | 10000 | 286,428.717 ns |   419.2247 ns |   392.1430 ns |  82.63 |    0.32 |    5 |     - |     - |     - |       2 B |
|     Reflection | 10000 | 945,775.059 ns | 3,251.6193 ns | 3,041.5667 ns | 272.83 |    1.31 |    6 |     - |     - |     - |         - |
|           Func | 10000 |  20,592.858 ns |    61.1335 ns |    57.1843 ns |   5.94 |    0.02 |    2 |     - |     - |     - |         - |
| ExpressionFunc | 10000 |  43,066.526 ns |   799.1496 ns |   747.5250 ns |  12.42 |    0.23 |    3 |     - |     - |     - |         - |
|        Dynamic | 10000 |  84,342.563 ns |   898.8935 ns |   840.8256 ns |  24.33 |    0.24 |    4 |     - |     - |     - |         - |
