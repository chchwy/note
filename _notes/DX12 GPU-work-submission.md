#GPU #DX12

早年驅動 GPU 畫圖的方法相當單純，設定好渲染管線參數，呼叫 `Draw()`，GPU 就會把東西畫出來。在 [[DX12]] 等低階 API 出現後，事情變得有一點複雜。

如果從 [[DX11]] 來看，首先是 DeviceContext 物件消失了，原本 DeviceContext 負責的工作，切割成數塊，由數個不同物件各自承擔下來。

### Command Queue：CPU/GPU 溝通的管道

首先是 Command Queue。Command Queue 是一個先進先出的管道。CPU 從一頭塞入命令，GPU 從 Command queue 另一頭依序取出命令並執行。

### Command List 錄製命令
該怎麼向 GPU 提交命令呢？

然後建立 Command List 以及 Command Allocator。用 Command List 錄製命令。僅僅是在 CPU 端錄製，GPU 命令還不會被執行。

### 非同步執行

接下來就把 Command List submit 到 Command Queue。就算提交了，命令也不會馬上執行，API 呼叫會馬上返回，射後不理。

這個錄製命令的動作，可以想像為一個快餐店的櫃檯正在為客戶那邊餐。  
  
記錄客戶想要吃什麼一個大叔一個漢堡飲料是可樂等等，但是直到櫃檯按出送出菜單，之前後腸子都還不會開始製作餐點。  
  
CPU和gpu的協同工作協同工作。 可以想像成一個快餐店的櫃檯跟後長的配合後長的配合。  
  
CPU完成點餐之後，他可以馬上會下一位客戶點餐，不需要等待請個客戶的餐點完成。 CPU就像gpu。 就像。  
  
CPU就像餐廳的後場。  
  
依序製作從前面櫃檯送來的單子。  
  
減少CPU跟gpu互相等待的時間。

### 為什麼要這樣設計？

好處是什麼呢？
1. 可以使用多個 thread 來同時錄製 GPU commands。充分利用現代 CPU 的多核心能力
2. 減少 CPU/GPU 互相等待的時間。增加同步工作的效率。


### 同步 CPU/GPU

如果需要知道 GPU 到底執行到哪個階段了，就要透過 Fence 物件來取得同步資訊。

提交一個階段的工作後，塞入一個 fence 信號 （注意！這也是個非同步 API call）
```
UINT fenceValue = 5
commandQueue->Signal(mainFence, fenceValue);
```

接著可以在後續的地方呼叫
```
mainFence->GetCompletedValue(); 
```
就可以得知該信號之前的命令是否已經執行完畢。