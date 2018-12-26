#### 题目描述
求一个无序数组的第k小元素

#### 解题思路
借鉴快速排序的划分思想  
设数组A[0:n-1]  
1. 对数组进行划分，使得基准元素小于其左边的数，大于其右边的数，得到基准元素最终的位置pivot及相对位置pos（表示当前数组的第pos小的元素位置）
2. 若pos = k，则返回基准元素A[pivot]
3. 若pos < k，则第k小元素一定在数组右半部分，即求A[pivot+1:n-1]的第k-pos小的元素，递归执行第1步
4. 若pos > k，则第k小元素一定在数组左半部分，即求A[0:pivot-1]的第k小元素，递归执行第1步

最好的情况下，时间复杂度为O(logn)

#### 代码实现
[code](/DivideAndConquer/find_k_th.cpp)  
```
int findKth(int A[], int s, int e, int k)
{
	// 一次划分后基准元素最终的位置
	int pivot = partition(A, s, e);
	// 基准元素在当前数组中的相对位置，即数组的第pos小元素
	int pos = pivot - s + 1;

	if(pos == k)
	{
		return A[pivot];
	}
	else if(pos < k)
	{
		return findKth(A, pivot + 1, e, k - pos);
	}
	else
	{
		return findKth(A, s, pivot - 1, k);
	}
}
```