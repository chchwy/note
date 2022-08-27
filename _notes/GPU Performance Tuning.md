#GPU #Shader #Benchmark 
Source: https://developer.apple.com/documentation/metal/performance_tuning

這是從蘋果的 Metal 文件摘錄出來的，幾個優化 GPU 效能的下刀處：

1.  GPU's Shader Occupancy

[Finding Your App's GPU GPU Shader Occupancy](https://developer.apple.com/documentation/metal/performance_tuning/finding_your_app_s_gpu_shader_occupancy)

看看各個不同階段的硬體單元，佔用的情況。佔用比太低或太高都不行。可以適當地調配各個不同種類的 shader 工作分擔。

2. Reducing Shader Bottlenecks

3. Measuring the GPU's Use of Memory Bandwidth

