#DX12 #DXGI 
Source: [[Book-Introduction to Game Programming With DirectX 12]] Ch 4.1

DXGI Display Adapter 係一個實現了渲染功能的硬體，那個硬體有 99% 的機率名叫「顯示卡」。除了顯示卡之外，也有軟體模擬的 software adapter (Windows 8 之後)。

列舉所有 DXGI Adapters 的方法：

```cpp
void D3DApp::LogAdapters()
{
    UINT i = 0;
	IDXGIAdapter* adapter = nullptr;
	std::vector<IDXGIAdapter*> adapterList;
	while(dxgiFactory->EnumAdapters(i, &adapter) != DXGI_ERROR_NOT_FOUND)
	{
		DXGI_ADAPTER_DESC desc;
		adapter->GetDesc(&desc);
		
		std::wstring text = L"***Adapter: ";
		text += desc.Description;
		text += L"\n";
		
		OutputDebugString(text.c_str());
		
		adapterList.push_back(adapter);
		
		++i;
	}
	
	for(size_t i = 0; i < adapterList.size(); ++i)
	{
		LogAdapterOutputs(adapterList[i]);
		ReleaseCom(adapterList[i]);
	}
}
```
