#Algo 

快慢指針，是一種操作陣列/鏈結串列的手法。

使用兩個 Pointers，一個在前先走，一個在後晚點走。使用快慢指針，有時候可以把O(N^2) 的解法降到O(N)，避免多次循環重複參訪同一個陣列。

一個經典的例子是：有序陣列移除重複元素。

```
1 3 4 4 4 5 7
  ^     ^
  slow  fast
```

用 slow/fast pointers 就可以只走一遍。

不需要用雙重迴圈
```
for i to N
  for j to N
    if elem[i] == elem[j]
      remove elem[j]
```
