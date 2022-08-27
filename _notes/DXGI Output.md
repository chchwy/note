#DX12 #DXGI
Source: [[Book-Introduction to Game Programming With DirectX 12]] Cht 4.1.10


每個 [[DXGI Adapter]] 之下，都會有一個或多個 Display Output (物件型態為 `IDXGIOutput` )，那個東西通常叫做螢幕。

如果一張顯卡 (Adapter) 接了兩個螢幕，那麼就會有兩個 Outputs

列舉某張顯卡下的所有螢幕：

```cpp
void D3DApp::LogAdapterOutputs(IDXGIAdapter* adapter) 
{ 
  UINT i = 0; 
  IDXGIOutput* output = nullptr; 
  while(adapter->EnumOutputs(i, &output) != DXGI_ERROR_NOT_FOUND) 
  { 
    DXGI_OUTPUT_DESC desc; 
    output->GetDesc(&desc); 
     
    std::wstring text = L"***Output: "; 
    text += desc.DeviceName; 
    text += L"\n"; 
    OutputDebugString(text.c_str()); 
  
    LogOutputDisplayModes(output, DXGI_FORMAT_B8G8R8A8_UNORM); 
  
    ReleaseCom(output); 
  
    ++i; 
  } 
}
```