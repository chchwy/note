#GPU #DX12 

通常 CPU 傳送給 GPU 的指令，都會透過第一條 Command Queue 。也叫做 3D Queue / Direct Queue / Graphics Queue。可以調動所有的 GPU 硬體資源。

除了第一條 Graphics Queue 以外，還可以建立第二條或更多的 Command Queue。

建立 Compute Queue 的目的是最大化利用 GPU 的硬體資源。當 Graphics Queue 正在進行其他重度工作時，可以順便利用閒置的 compute unit。

Compute Queue 是一種能力比較受限的 Command Queue。相較於 Graphics Queue 只能夠調用 compute shader 相關的硬體資源。

Compute Queue 不能處理以下種類的 resource barriers
- Depth Read/Write
- Render Target View
- Pixel Shader Resource



References:
- [ID3D12Device::CreateCommandQueue method](https://docs.microsoft.com/en-us/windows/win32/api/d3d12/nf-d3d12-id3d12device-createcommandqueue)