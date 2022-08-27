---
aliases: [二分搜尋法, Binary Search]
---

#Algo #Cpp #CodeSnippet 

Time Complexity: Big-O(logN)

已排序好的陣列裡快速定位元素，用 NLogN 的時間。

解題的關鍵在於定義搜尋的區間：[left, right]

在我的解法裡面 left 和 right 都是有效的位置。所以 while 的判斷式要用 while(left <= right)，因為 left == right 是有意義的。

想法：先確認位於範圍中間的元素。
終止條件：中間的元素就是我們要找的元素。

我的 C++ 版本
```cpp

int binary_search(vector<int> nums, int target)
{
	int left = 0;
	int right = nums.size() - 1;
	int mid = (left + right) / 2;

	while(left <= right)
	{
		if (nums[mid] == target)
		{
			return mid;
		}
		else if (nums[mid] > target) 
		{
			right = mid - 1;
		}
		else
		{
			left = mid + 1;
		}
		mid = (left + right) / 2;
	}
	return -1; // couldn't find it
}
```
