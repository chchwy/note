#GPU #DX12 

Async Compute 是同時執行多個工作，充分利用 GPU 資源，改善效能的手法。

在 [[DX12]] 裡，Async Compute 的用方是建立兩個以上的 [[DX12 Command Queue]]。除了原本的 3D Queue (或者叫Direct Queue)，再另外建立一個 [[Compute Queue]]。

當主要的 3D Queue 正在執行其他工作，而 Compute Unit 閒置時，Compute Queue 可以利用閒置的資源跑 Compute shader。
