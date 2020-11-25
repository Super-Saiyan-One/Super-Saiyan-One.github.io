---
title: AcWing 786.第k个数（快速选择）
url: AcWing.786_url
tags:
  - 分治
  - 排序
categories:
  - 排序算法
date: 2020-08-013 20:03:00
---
# 快速排序
**快速排序**即sort方法的手动实现
1. 确定当前区间的左端点l，右端点r，并取x=q[(l+r)/2]
2. 运用双指针调整区间，使得区间左半边的值都<=x，右半边区间的值都>=x
3. 不断递归
本题目与快速排序算法基本相同，由于要找出第k小的数，估值需要判断k在左区间还是右区间，只需要递归k所在的区间即可。复杂度：O(n)

```c++
#include <iostream>
#include <algorithm>
using namespace std;
const int N =1e6+10;
int q[N];
int n,k;
int quick_sort(int l,int r,int k)
{
	if(l==r) return q[l];
	int x=q[(l+r)/2],i=l-1,j=r+1;
	while(i<j)
	{
		do i++; while(q[i]<x);
		do j--; while(q[j]>x);
		if(i<j) swap(q[i],q[j]);
	}
	int sl=j-l+1;
	if(k<=sl) return quick_sort(l,j,k);
	return quick_sort(j+1,r,k-sl);
	
}
int main()
{
	cin>>n>>k;
	for(int i=0;i<n;i++) cin>>q[i];
	
	printf("%d\n",quick_sort(0,n-1,k));
} 
```

<!-- more -->
