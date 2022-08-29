#Cpp #Benchmark #CodeSnippet
[[C++]] Benchmarking

C++11 測量程式執行時間的方法

```cpp
using std::chrono::high_resolution_clock;  
using std::chrono::duration_cast;  
using std::chrono::duration;  
using std::chrono::microseconds;  

auto t1 = high_resolution_clock::now();  

// Your task!

auto t2 = high_resolution_clock::now();  
auto ms_int = duration_cast<microseconds>(t2 - t1);  

cout << "The task takes" << ms_int.count();
```
