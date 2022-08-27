#DX12 

ID3D12Fence

[[DX12]] Fence is a way to synchronize the work between CPU and GPU.

生活例子：發號碼牌。CPU 抽了一張號碼牌，然後問 GPU，現在到幾號了阿？

問法： `ID3D12Fence::GetCompletedValue()`

`ID3D12Fence::GetCompletedValue()` returns `UINT64_MAX` if the device is removed.