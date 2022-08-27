#DX12 #GPU 

[[DX12]] 連結CPU/GPU的命令通道

We must know that with graphics programming we have two processors at work: CPU and GPU.

3D 圖形學程式裡，有兩個處理器同時在工作：CPU 和 GPU。兩個處理器各自獨立作業，但是必要時也是要交流一下。

多數時候 CPU 單向告知 GPU。CPU 發出指令，指示 GPU 該如何渲染畫面，GPU 完成工作後，輸出到螢幕。

溝通的橋樑叫做 Command Queue。CPU 把要執行的指令，送入 Command Queue，而 GPU 則從 Command Queue 取出指令並依序執行。

Command Queue 是一個先進先出的管道。

Command Queue 可已有三種類型:
1. Direct Queue (或者叫 Graphics Queue, 3D Queue)
2. [[Compute Queue]]
3. Copy Queue

由上到下，上面權力最大，下面權力最小。
