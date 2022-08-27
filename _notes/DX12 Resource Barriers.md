#DX12 #TODO 

在 [[DX12]] 裡，Resource Barrier 是用來提示 GPU 資源使用的方式要改變了。

References:
https://devblogs.microsoft.com/directx/a-look-inside-d3d12-resource-state-barriers/

https://docs.microsoft.com/en-us/windows/win32/direct3d12/using-resource-barriers-to-synchronize-resource-states-in-direct3d-12


## Debugging Resource states

[DebugCommandQueue::AssertResourceState](https://docs.microsoft.com/en-us/windows/win32/api/d3d12sdklayers/nf-d3d12sdklayers-id3d12debugcommandqueue-assertresourcestate)
[DebugCommandList::AssertResourceState](https://docs.microsoft.com/en-us/windows/win32/api/d3d12sdklayers/nf-d3d12sdklayers-id3d12debugcommandlist1-assertresourcestate)
