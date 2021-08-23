[TOC]

# 数据结构与算法

## 排序

**排序的定义**

假设含有n个记录的序列为{r1,r2,...,rn}，其相应的关键字分别是{k1,k2,...,kn}，需要确定1,2,...,n的一种排列p1,p2,...,pn，使其相应的关键字满足kp1<=kp2<=...<=kpn 非递减（或非递增）的关系，即使得序列成为一个按关键字有序的序列{rp1,rp2,...,rpn}，这样的操作就称为排序[1]。

简单来说，排序就是使输入的序列变成符合一定规则（关键字）的有序序列（非递减或非递增）。大多数遇到的排序问题都是按数据元素值的大小规则进行排序的问题。所以本文为了方便起见，只讨论数据元素值大小比较的排序问题。

**排序的稳定性**

假设ki=kj（1<=i《=n，1<=j<=n，i!=j），且在排序前的序列中ri领先于rj（即i<j）。

- 如果排序后ri仍领先于rj，则称所用的排序方法是稳定的；
- 反之，若可能使得排序后的序列中rj领先于ri，则称所用的排序方法是不稳定的。

简单来概括稳定和不稳定[2]：

- **稳定**：如果a原本在b前面，而a=b，排序之后a仍然在b前面；
- **不稳定**：如果a原本在b前面，而a=b，排序之后a可能在b的后面。

**时间和空间复杂度**

- **时间复杂度**：对排序数据的总的操作次数。反应当n变化时，操作次数呈现什么规律
- **空间复杂度**：算法在计算机内执行时所需要的存储空间的容量，它也是数据规模n的函数。

### 排序算法

排序算法可以分成两大类：

**非线性时间比较类排序**：通过比较来决定元素间的相对次序，由于其时间复杂度不能突破O(nlogn)，因此称为非线性时间比较类排序。

**线性时间非比较类排序**：不通过比较来决定元素间的相对次序，它可以突破基于比较排序的时间下界，以线性时间运行，因此称为线性时间非比较类排序。

- [`冒泡排序（Bubble Sort`](https://github.com/amusi/coding-note/tree/master/Data%20Structures%20and%20Algorithms/sort#bubblesort)
- [`选择排序（Selection Sort`](https://github.com/amusi/coding-note/tree/master/Data%20Structures%20and%20Algorithms/sort#selectionsort)
- [`插入排序（Insertion Sort`](https://github.com/amusi/coding-note/tree/master/Data%20Structures%20and%20Algorithms/sort#insertionsort)
- [`希尔排序（Shell Sort`](https://github.com/amusi/coding-note/tree/master/Data%20Structures%20and%20Algorithms/sort#shellsort)
- [`堆排序（heap Sort`](https://github.com/amusi/coding-note/tree/master/Data%20Structures%20and%20Algorithms/sort#heapsort)
- [`归并排序（merge Sort`](https://github.com/amusi/coding-note/tree/master/Data%20Structures%20and%20Algorithms/sort#mergesort)
- [`快速排序（Fast Sort`](https://github.com/amusi/coding-note/tree/master/Data%20Structures%20and%20Algorithms/sort#fastsort)

### 常见排序算法复杂度

[![常用排序算法1](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/sort_algorithms_1.png)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/sort_algorithms_1.png)

[![常用排序算法2](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/sort_algorithms_2.png)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/sort_algorithms_2.png)

- [8大排序算法稳定性分析](https://www.cnblogs.com/codingmylife/archive/2012/10/21/2732980.html)



### 冒泡排序（Bubble Sort）

**基本思想**

比较相邻的两个元素，将值大的元素交换到右边（降序则相反）

**步骤：**

1. 比较相邻的元素。如果第一个比第二个大，就交换它们两个；
2. 对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对，这样在最后的元素应该会是最大的数；
3. 针对所有的元素重复以上的步骤，除了最后一个；
4. 重复步骤1~3，直到排序完成。

比如有n个元素，那么第一次比较迭代，需要比较n-1次（因为是相邻成对比较，最后一个元素没有与下一个相邻比较的对象，所以是n-1次），此次迭代完成后确定了最后一个元素为最大值；第二次比较迭代，需要比较n-2次，因为第一次迭代已经确定好了最后一个元素，所以不再需要比较；...；第 i次比较迭代，需要比较n-i次，此时确定后面i个元素是有序的较大元素；...；第n-1次比较迭代，需要比较n-(n-1)次，此时完成冒泡排序操作。

时间复杂度：o(n^2) = (n-1)*(n-1)

**动图演示：**

![bubble_sort](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/bubble_sort_1.jpg)

![bubble_sort](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/bubble_sort.gif)

**过程演示：**待排序数组：{5, 4, 7, 1, 6, 2}，升序排序

\---------------------------------------

第一次循环：

第一次比较5和4，5>4，交换位置：{4，5，7，1，6，2}

第二次比较5和7，5

第三次比较7和1，7>1，交换位置：{4，5，1，7，6，2}

第四次比较7和6，7>6，交换位置：{4，5，1，6，7，2}

第五次比较7和2，7>2，交换位置：{4，5，1，6，2，7}

第一次循环完成结果：{4，5，1，6，2，7}

\----------------------------------------

第二次循环：

第一次比较4和5，4

第二次比较5和1，5>1，交换位置：{4，1，5，6，2，7}

第三次比较5和6，5

第四次比较6和2，6>2，交换位置：{4，1，5，2，6，7}

第五次比较6和7，6

第二次循环完成结果：{4，1，5，2，6，7}

\----------------------------------------

第三次循环：

第一次比较4和1，4>1，交换位置：{1，4，5，2，6，7}

第二次比较4和5，4

第三次比较5和2，5>2，交换位置：{1，4，2，5，6，7}

第四次比较5和6，5

第五次比较6和7，6

第三次循环完成结果：{1，4，2，5，6，7}

\----------------------------------------

第四次循环：

第一次比较1和4，1

第二次比较4和2，4>2，交换位置：{1，2，4，5，6，7}

第三次比较4和5，4

第四次比较5和6，5

第五次比较6和7，6

第三次循环完成结果：{1，2，4，5，6，7}

\----------------------------------------

第五次循环：

第一次比较1和2，1

第二次比较2和4，2

第三次比较4和5，4

第四次比较5和6，5

第五次比较6和7，6

第三次循环完成结果：{1，2，4，5，6，7}

相信看完上面的演示过程，你对冒泡排序过程及原理有了完全的理解，但是细心的朋友应该会发现其实在第四次循环就已经得到了最终的结果，这么来看第五次循环完全是多余的，于是就有冒泡排序的改进版本：当某一轮循环当中没有交换位置的操作，说明已经排好序了，就没必要再循环了，break退出循环即可。

**复杂度分析：**

- 时间复杂度：若给定的数组刚好是排好序的数组，采用改进后的冒泡排序算法，只需循环一次就行了，此时是最优时间复杂度：O(n)，若给定的是倒序，此时是最差时间复杂度：O(n^2) ，因此综合平均时间复杂度为：O(n^2)
- 空间复杂度：因为每次只需开辟一个temp的空间，因此空间复杂度是：O(1)

**代码实现：**

- 

- [bubble_sort.cpp](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/code/bubble_sort.cpp)

```
/* Summary: 冒泡排序
* Author: Amusi
* Date:   208-05-27
*
* Reference: 
*	http://en.wikipedia.org/wiki/Bubble_sort
*	https://github.com/xtaci/algorithms/blob/master/include/bubble_sort.h
*   https://zhuanlan.zhihu.com/p/37077924
*
* 冒泡排序说明：比较相邻的两个元素，将值大的元素交换到右边（降序则相反）
*
*/

#include <iostream>

// 冒泡函数
namespace alg{
	template<typename T>
	static void BubbleSort(T list[], int length)
	{

#if 1
		// 版本1：两层for循环 
		for (int i = 0; i < length-1; ++i)
		{ 
			for (int j = 0; j < length - i -1; ++j)
			{
				// 两两相邻元素比较大小，从小到大排序
				// if (list[j] < list[j + 1]) : 从大到小排序
				if (list[j] > list[j + 1])
				{
					int temp = list[j + 1];
					list[j + 1] = list[j];
					list[j] = temp;
				}
			}
		}

#else
		// 版本2：while+一层for循环
		bool swapped = false;
		while (!swapped)
		{
			swapped = true;
	
			for (int i = 0; i < length - 1; ++i)
			{
				// 两两相邻元素比较大小，从小到大排序
				// if (list[j] < list[j + 1]) : 从大到小排序
				if (list[i] > list[i + 1])
				{
					int temp = list[i + 1];
					list[i + 1] = list[i];
					list[i] = temp;
				}
				swapped = false;
			}
			length--;
		}
			
#endif

	}
}

using namespace std;
using namespace alg;


int main()
{
	int a[8] = { 5, 2, 5, 7, 1, -3, 99, 56 };
	BubbleSort<int>(a, 8);
	for (auto e : a)
		std::cout << e << " ";

	return 0;
}
```

- [bubble_sort.py](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/code/bubble_sort.py)

```
''' Summary: 冒泡排序
* Author: Amusi
* Date:   208-05-27
*
* Reference: 
*	http://en.wikipedia.org/wiki/Bubble_sort
*	https://github.com/xtaci/algorithms/blob/master/include/bubble_sort.h
*   https://zhuanlan.zhihu.com/p/37077924
*
* 冒泡排序说明：比较相邻的两个元素，将值大的元素交换到右边（降序则相反）
*
'''

def BubbleSort(array):
    lengths = len(array)
    for i in range(lengths-1):
        for j in range(lengths-1-i):
            if array[j] > array[j+1]:
               array[j+1], array[j] = array[j], array[j+1]

    return array


array = [1,3,8,5,2,10,7,16,7,4,5]
print("Original array: ", array)
array = BubbleSort(array)
print("BubbleSort: ", array)
```

**参考：**

1 [经典排序算法之冒泡排序](http://baijiahao.baidu.com/s?id=1585931471155461767&wfr=spider&for=pc)

2 (图示版)：[来、通俗聊聊冒泡排序](https://zhuanlan.zhihu.com/p/37077924)



### 选择排序（Selection Sort）

**基本思想**

首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置，然后，再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。以此类推，直到所有元素均排序完毕。

**步骤**

n个记录的直接选择排序可经过n-1趟直接选择排序得到有序结果。具体算法描述如下：

- 初始状态：无序区为R[1..n]，有序区为空；
- 第i趟排序(i=1,2,3…n-1)开始时，当前有序区和无序区分别为R[1..i-1]和R(i..n）。该趟排序从当前无序区中-选出关键字最小的记录 R[k]，将它与无序区的第1个记录R交换，使R[1..i]和R[i+1..n)分别变为记录个数增加1个的新有序区和记录个数减少1个的新无序区；
- n-1趟结束，数组有序化了。

**动图演示**

![selection_sort](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/selection_sort.gif)

**复杂度分析**

- 时间复杂度：O(n2)

  注：无论什么数据进去，选择都是O(n2)的时间复杂度，所以若要使用它，建议数据规模越小越好。

- 空间复杂度：O(1)


**代码实现**

- 

- [selection_sort.cpp](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/code/selection_sort.cpp)

```
/* Summary: 选择排序
* Author: Amusi
* Date:   208-06-22
*
* Reference: 
*   https://en.wikipedia.org/wiki/Selection_sort
*   https://github.com/xtaci/algorithms/blob/master/include/selection_sort.h
* 选择排序说明：首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置，然后，再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。以此类推，直到所有元素均排序完毕。 
*
*/

#include <iostream>

// 选择排序函数
namespace alg{
	template<typename T>
	static void SelectionSort(T list[], int length)
	{
		// 外循环: length-1次，因为当length-1个元素排序好后，第length个元素位置不再变化
		for (int i = 0; i < length-1; ++i)
		{ 
			int minIndex = i;
			// 从i的位置，进行遍历，因为前i-1个元素已经排序好
			for (int j = i; j < length; ++j)
			{
				// 每次从未排序的数组中选出最小的值放入已排序的数组中，即从小到大排序
				if (list[j] < list[minIndex])
				{
					minIndex = j;
				}
			}
			int temp = list[minIndex];
			list[minIndex] = list[i];
			list[i] = temp;
		}

	}
}

using namespace std;
using namespace alg;


int main()
{
	int a[8] = { 5, 2, 5, 7, 1, -3, 99, 56 };
	SelectionSort<int>(a, 8);
	for (auto e : a)
		std::cout << e << " ";

	return 0;
}
```

- [selection_sort.py](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/code/selection_sort.py)

```
''' Summary: 选择排序
* Author: Amusi
* Date:   208-06-22
*
* Reference: 
*   https://en.wikipedia.org/wiki/Selection_sort
*
* 选择排序说明：首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置，然后，再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。以此类推，直到所有元素均排序完毕。 
*
'''

def SelectionSort(array):
    lengths = len(array)
    for i in range(lengths-1):
        min_index = i
        for j in range(i, lengths):
            if array[j] < array[min_index]:
               min_index = j
        array[i], array[min_index] = array[min_index], array[i]
		
    return array


array = [1,3,8,5,2,10,7,16,7,4,5]
print("Original array: ", array)
array = SelectionSort(array)
print("SelectionSort: ", array)
```



### 插入排序（Insertion Sort）

**基本思想**

插入排序（insertion sort）又称直接插入排序（staright insertion sort），其是将未排序元素一个个插入到已排序列表中。对于未排序元素，在已排序序列中从后向前扫描，找到相应位置把它插进去；在从后向前扫描过程中，需要反复把已排序元素逐步向后挪，为新元素提供插入空间。

**步骤**

1. 从第一个元素开始，该元素可以认为已经被排序；
2. 取出下一个元素（未排序），在已经排序的元素序列中从后向前扫描；
3. 如果该元素（已排序）大于新元素，将该元素移到下一位置（往前移动）；
4. 重复步骤3，直到找到已排序的元素小于或者等于新元素的位置；
5. 将新元素插入到该位置后；
6. 重复步骤2~5。

**动图演示**

![插入排序图示](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/insertion_sort.gif)

**复杂度分析**

- 时间复杂度：最坏O(n2)、平均O(n2)、最好O(n)
- 空间复杂度：O(n1)
- 稳定性：稳定

举个例子（暴力手绘图）

![Insertion Sort](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/insertion_sort.png)

**代码实现**

- [insertion_sort.cpp](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/code/insertion_sort.cpp)

```
/* Summary: 插入排序（Insertion Sort）
* Author: Amusi
* Date:   2018-07-16
*
* Reference: 
*   https://en.wikipedia.org/wiki/Insertion_sort
*	
* 插入排序（insertion sort）又称直接插入排序（staright insertion sort），其是将未排序元素一个个插入到已排序列表中。对于未排序元素，在已排序序列中从后向前扫描，找到相应位置把它插进去；在从后向前扫描过程中，需要反复把已排序元素逐步向后挪，为新元素提供插入空间。
*
*/

#include <iostream>

// 插入排序函数
namespace alg{
	template<typename T>
	static void InsertionSort(T list[], int length)
	{
		// 从索引为1的位置开始遍历
		for (int i = 1; i < length; ++i)
		{
			T currentValue = list[i];	// 保存当前值
			int preIndex = i - 1;	// 前一个索引值
			// 循环条件: 前一个索引值对应元素值大于当前值 && 前一个索引值大于等于0
			while (list[preIndex] > currentValue && preIndex >= 0){
				list[preIndex + 1] = list[preIndex];
				preIndex--;
			}
			list[preIndex + 1] = currentValue;
		}
	}
}

using namespace std;
using namespace alg;


int main()
{
	int a[8] = { 5, 2, 5, 7, 1, -3, 99, 56 };
	InsertionSort<int>(a, 8);
	for (auto e : a)
		std::cout << e << " ";

	return 0;
}
```

- [insertion_sort.py](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/code/insertion_sort.py)

```
''' Summary: 插入排序（Insertion Sort）
* Author: Amusi
* Date:   208-07-16
*
* Reference: 
*   https://en.wikipedia.org/wiki/Insertion_sort
*   https://www.cnblogs.com/wujingqiao/articles/8961890.html
*	
* 插入排序（insertion sort）又称直接插入排序（staright insertion sort），其是将未排序元素一个个插入到已排序列表中。对于未排序元素，在已排序序列中从后向前扫描，找到相应位置把它插进去；在从后向前扫描过程中，需要反复把已排序元素逐步向后挪，为新元素提供插入空间。
*
'''

def InsertionnSort(array):
    lengths = len(array)
    # 从索引位置1开始
    for i in range(1, lengths):
        currentValue = array[i] # 当前索引对应的元素数值
        preIndex = i-1		     # 前一个索引位置
        # 循环条件: 前一个索引对应元素值大于当前值，前一个索引值大于等于0
        while array[preIndex] > currentValue and preIndex>=0:
        	array[preIndex+1] = array[preIndex]	# 前一个索引对应元素值赋值给当前值
        	preIndex -= 1	# 前一个索引位置-1
        # preIndex+1，实现元素交换
        array[preIndex+1] = currentValue
		
    return array


array = [1,3,8,5,2,10,7,16,7,4,5]
print("Original array: ", array)
array = InsertionnSort(array)
print("InsertionnSort: ", array)
```



### 希尔排序（Shell Sort）

**基本思想**

设待排序元素序列有n个元素，首先取一个整数increment（小于n）作为间隔将全部元素分为increment个子序列，所有距离为increment的元素放在同一个子序列中，在每一个子序列中分别实行直接插入。

注：在[希尔排序算法](https://en.wikipedia.org/wiki/Shellsort)提出之前，排序算法的时间复杂度都为O(n^2)，如冒泡排序、选择排序和插入排序。而希尔排序算法是突破这个时间复杂度的第一批算法之一。该复杂度为O(nlogn)，其实直接插入排序算法的改进版，也称为缩小增量排序。**希尔排序是直接插入排序的一种改进，减少了其复制的次数，速度要快很多**。原因是，当n值很大时，数据项每一趟排序需要移动的个数很少，但数据项的距离很长；当n值减小时，每一趟需要移动的数据增多。正是因为这两种情况的结合才使得希尔排序效率比插入排序高很多。

**步骤**

先将整个待排序的记录序列分割成为若干子序列分别进行直接插入排序，具体算法描述：

- 选择一个增量序列t1，t2，…，tk
- 按增量序列个数k，对序列进行k 趟排序；
- 每趟排序，根据对应的增量ti，将待排序列分割成若干长度为m 的子序列，分别对各子表进行直接插入排序。仅增量因子为1 时，整个序列作为一个表来处理，表长度即为整个序列的长度。

注：增量的初始值一般为序列长度的一半，然后之后每次再自身减半。

**动图演示**

[![希尔排序](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/shell_sort01.gif)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/shell_sort01.gif)

上图是不是很难理解，那么来看看这个！

[![img](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/shell_sort02.png)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/shell_sort02.png)

说实话，看了上面两个图，我还是有点不理解，不怕，我又找了下面这幅图像。

简单介绍一下：

对于[592, 401, 874, 141, 348, 72, 911, 887, 820, 283]序列，一共10个元素。

**第一次，设置增量为5=10/2**，所以有5个子序列：[592,72]、[401,911]、[874,887]、[141,820]和[348,283]。然后对每个子序列进行插入排序，结果是[72,592]、[401,911]、[874,887]、[141,820]和[283,348]。注意，这些元素在序列中的位置初始是不变的，只会随着部分子序列间元素的位置变化而变化，比如[592,72]在原来的序列中索引是[0,5]，之后变成了[5,0]；而[401,911]的序列索引是[1,6]，第一次处理后，索引值不变。

总之，第一次处理的结果是将**[592, 401, 874, 141, 348, 72, 911, 887, 820, 283]—> [72, 401, 874, 141, 283, 592, 911, 887, 820, 348]**。

**第二次，设置增量为2=5/2**，所以有2个子序列：[72, 874, 283, 911, 820]和[401, 141, 592, 887, 348]。然后对每个子序列进行插入排序，[72, 874, 283, 911, 820]的结果是[72, 283, 820, 874, 911]，而[401, 141, 292, 887, 348]的结果是[141, 292, 348, 401, 887]。

总之，第二次处理的结果是将 **[72, 401, 874, 141, 283, 592, 911, 887, 820, 348]—>[72, 141, 283, 292, 820, 348, 874, 401, 911, 997]**。

**第三次，设置增量为1=2/2**，所以有1个序列，就是上述生成的序列[72, 141, 283, 292, 820, 348, 874, 401, 911, 997]。然后进行插入排序，其结果为[72, 141, 283, 292, 348, 401, 820, 874, 911, 997]。

总之，第三次处理的结果是将 **[72, 141, 283, 292, 820, 348, 874, 401, 911, 997]—>[72, 141, 283, 292, 348, 401, 820, 874, 911, 997]**。

其实本质上还是利用了插入排序，但这里通过增量作用，相当于添加了预处理，减少插入排序中移动元素的次数，提高了效率。通过"增量"预处理，使得希尔排序算法时间复杂度降低。

[![img](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/shell_sort03.jpg)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/shell_sort03.jpg)

**复杂度分析**

希尔排序的时间复杂度与增量序列的选取有关。

时间复杂度：

- 平均：O(n^1.3)
- 最差：O(n2)
- 最好：O(n)

空间复杂度：O(1)

稳定性：不稳定

**代码实现**

[shell_sort.cpp](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/code/shell_sort.cpp)

```
/* Summary: 希尔排序（Shell Sort）
* Author: Amusi
* Date:   2018-09-23
*
* Reference:
*   https://en.wikipedia.org/wiki/Shellsort
*   https://www.geeksforgeeks.org/shellsort/
*   希尔排序（shell sort）：设待排序元素序列有n个元素，首先取一个整数increment（小于n）作为间隔将全部元素分为increment个子序列，所有距离为increment的元素放在同一个子序列中，在每一个子序列中分别实行直接插入。
*
*/

#include <iostream>

// 希尔排序函数（基于快速插入排序）
namespace alg{
	template<typename T>
	static void ShellSort(T list[], int n)
	{
		// 设置增量：以n/2为初始gap，然后逐渐减小gap（每次缩小为上次gap的一半）
		for (int gap = n / 2; gap > 0; gap /= 2){
			// 遍历当前趟，对每个子序列进行插入排序
			for (int i = gap; i < n; i++){
				int temp = list[i];
				int j = 0;
				// 遍历子序列
				for (j = i; j >= gap && list[j - gap]>temp; j -= gap)
					list[j] = list[j - gap];

				list[j] = temp;
			}
		}
	}
}

using namespace std;
using namespace alg;


int main()
{
	int a[8] = { 5, 2, 5, 7, 1, -3, 99, 56 };
	int n = sizeof(a) / sizeof(a[0]);
	ShellSort<int>(a, n);
	for (auto e : a)
		std::cout << e << " ";

	return 0;
}
```

[shell_sort.py](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/code/shell_sort.py)

```
'''
* Summary: 希尔排序（Shell Sort）
* Author: Amusi
* Date:   2018-09-23
*
* Reference:
*   https://en.wikipedia.org/wiki/Shellsort
*   https://www.geeksforgeeks.org/shellsort/
*   希尔排序（shell sort）：设待排序元素序列有n个元素，首先取一个整数increment（小于n）作为间隔将全部元素分为increment个子序列，所有距离为increment的元素放在同一个子序列中，在每一个子序列中分别实行直接插入。
*
*
'''

def ShellSort(array):
    lengths = len(array)
    # 初始化gap
    gap = lengths//2
    # 减少增量，遍历子序列进行插入排序
    while(gap > 0):
        for i in range(gap, lengths):
            # 
            temp = array[i]
            j = i
            # 子序列插入排序
            while j>=gap and array[j-gap]>temp:
                array[j] = array[j-gap]
                j -= gap

            array[j] = temp
        
        gap = gap//2
		
    return array


array = [1,3,8,5,2,10,7,16,7,4,5]
print("Original array: ", array)
array = ShellSort(array)
print("InsertionnSort: ", array)
```

参考：

- [Shell Sort](https://www.geeksforgeeks.org/shellsort/)
- [理解希尔排序的排序过程](https://blog.csdn.net/weixin_37818081/article/details/79202115)
- [图解排序算法(二)之希尔排序](https://www.cnblogs.com/chengxiao/p/6104371.html)

### 堆排序（Heap Sort）

**基本思想**

[堆排序（heap sort）](https://en.wikipedia.org/wiki/Heapsort)：将待排序序列构造成一个大顶堆，此时，整个序列的最大值就是堆顶的根节点。将其与末尾元素进行交换，此时末尾就为最大值。然后将剩余n-1个元素重新构造成一个堆，这样会得到n个元素的次小值。如此反复执行，便能得到一个有序序列了。

注：堆排序是一种选择排序，指利用堆这种数据结构所设计的一种排序算法。堆积是一个近似完全二叉树的结构，并同时满足堆积的性质：即子结点的键值或索引总是小于（或者大于）它的父节点。

在介绍堆排序之前，先了解一下什么是**堆（heap）**？

**堆**

堆是具有以下性质的完全二叉树：每个结点的值都大于或等于其左右孩子结点的值，称为大顶堆；或者每个结点的值都小于或等于其左右孩子结点的值，称为小顶堆。如下图：

[![堆结构](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/heap.png)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/heap.png)

同时，我们对堆的结点按层进行编号，将这种逻辑结构映射到数组中就是下面这个样子：

[![img](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/heap2.png)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/heap2.png)

该数组从逻辑上讲就是一个堆结构，我们用简单的公式来描述一下堆的定义就是：

**大顶堆：arr[i] >= arr[2i+1] && arr[i] >= arr[2i+2] **

**小顶堆：arr[i] <= arr[2i+1] && arr[i] <= arr[2i+2] **

ok，了解了这些定义。接下来，我们来看看堆排序的基本思想及基本步骤：

**步骤**

- 将初始待排序关键字序列(R1,R2….Rn)构建成大顶堆，此堆为初始的无序区；
- 将堆顶元素R[1]与最后一个元素R[n]交换，此时得到新的无序区(R1,R2,……Rn-1)和新的有序区(Rn),且满足R[1,2…n-1]<=R[n]；
- 由于交换后新的堆顶R[1]可能违反堆的性质，因此需要对当前无序区(R1,R2,……Rn-1)调整为新堆，然后再次将R[1]与无序区最后一个元素交换，得到新的无序区(R1,R2….Rn-2)和新的有序区(Rn-1,Rn)。不断重复此过程直到有序区的元素个数为n-1，则整个排序过程完成。

**动图演示**

[![堆排序](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/heap_sort.gif)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/heap_sort.gif)

看到这里，你可能还是晕乎乎的，下面看个讲解示例：

**步骤一 构造初始堆。将给定无序序列构造成一个大顶堆（一般升序采用大顶堆，降序采用小顶堆)。**

a.假设给定无序序列结构如下

[![img](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p1.png)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p1.png)

b.此时我们从最后一个非叶子结点开始（叶结点自然不用调整，第一个非叶子结点 arr.length/2-1=5/2-1=1，也就是下面的6结点），从左至右，从下至上进行调整。

[![img](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p2.png)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p2.png)

c.找到第二个非叶节点4，由于[4,9,8]中9元素最大，4和9交换。

[![img](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p3.png)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p3.png)

d.这时交换导致了子根[4,5,6]结构混乱，继续调整，[4,5,6]中6最大，交换4和6。

[![img](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p4.png)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p4.png)

此时，我们就将一个无需序列构造成了一个大顶堆。

**步骤二 将堆顶元素与末尾元素进行交换，使末尾元素最大。然后继续调整堆，再将堆顶元素与末尾元素交换，得到第二大元素。如此反复进行交换、重建、交换。**

a.将堆顶元素9和末尾元素4进行交换

[![img](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p5.png)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p5.png)

b.重新调整结构，使其继续满足堆定义

[![img](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p6.png)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p6.png)

c.再将堆顶元素8与末尾元素5进行交换，得到第二大元素8.

[![img](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p7.png)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p7.png)

后续过程，继续进行调整，交换，如此反复进行，最终使得整个序列有序

[![img](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p8.png)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/heap_p8.png)

再简单总结下堆排序的基本思路：

**a.将无需序列构建成一个堆，根据升序降序需求选择大顶堆或小顶堆;**

**b.将堆顶元素与末尾元素交换，将最大元素"沉"到数组末端;**

**c.重新调整结构，使其满足堆定义，然后继续交换堆顶元素与当前末尾元素，反复执行调整+交换步骤，直到整个序列有序。**

**复杂度分析**

堆排序整体主要由构建初始堆+交换堆顶元素和末尾元素并重建堆两部分组成。其中构建初始堆经推导复杂度为O(n)，在交换并重建堆的过程中，需交换n-1次，而重建堆的过程中，根据完全二叉树的性质，[log2(n-1),log2(n-2)...1]逐步递减，近似为nlogn。所以堆排序时间复杂度一般认为就是O(nlogn)级。

时间复杂度：

- 最差：O(nlogn)
- 平均：O(nlogn)
- 最优：O(nlogn)

空间复杂度：O(n)

稳定性：不稳定

**代码实现**

-  TODO

参考：

- [图解排序算法(三)之堆排序](https://www.cnblogs.com/chengxiao/p/6129630.html)
- [heap-sort](https://www.geeksforgeeks.org/heap-sort/)

### 归并排序（Merge Sort）

**基本思想**

[归并排序（merge sort）](https://en.wikipedia.org/wiki/Merge_sort)：

**步骤**

- [ ] TODO

### 快速排序（Quick Sort）

**基本思想**

[快速排序（quick sort）](https://en.wikipedia.org/wiki/Quicksort)：通过一趟排序将待排列表分隔成独立的两部分，其中一部分的所有元素均比另一部分的所有元素小，则可分别对这两部分继续重复进行此操作，以达到整个序列有序。（这个过程，我们可以使用递归快速实现）

**步骤**

快速排序使用分治法来把一个串（list）分为两个子串（sub-lists）。具体算法描述如下：

- 从数列中挑出一个元素，称为 “基准”（pivot），这里我们通常都会选择第一个元素作为prvot；
- 重新排序数列，将比基准值小的所有元素放在基准前面，比基准值大的所有元素放在基准的后面（相同的数可以到任一边）。这样操作完成后，该基准就处于新数列的中间位置，即将数列分成了两部分。这个操作称为分区（partition）操作；
- 递归地（recursive）把小于基准值元素的子数列和大于基准值元素的子数按上述操作进行排序。这里的递归结束的条件是序列的大小为0或1。此时递归结束，排序就完成了。

**动图演示**

[![Quick Sort](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/quick_sort.gif)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/quick_sort.gif)

**复杂度分析**

- 时间复杂度：
  - 平均情况：O(nlogn)
  - 最好情况：O(nlong)
  - 最坏情况：O(n^2) 其实不难理解，快排的最坏情况就已经退化为冒泡排序了！所以大家深入理解就会发现各个排序算法是相通的，学习时间久了你就会发现它们的内在联系！是不是很神奇哈～
- 空间复杂度：
  - 平均情况：O(logn)
  - 最好情况：O(logn)
  - 最坏情况：O(n)
- 稳定性：不稳定 （由于关键字的比较和交换是跳跃进行的，所以快速排序是一种不稳定的排序方法～）

举个例子（暴力手绘图）

[![img](https://github.com/amusi/coding-note/raw/master/Data%20Structures%20and%20Algorithms/sort/images/quick_sort.png)](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/images/quick_sort.png)

**代码实现**

注：下面都是利用递归法实现快速排序。

[quick_sort.cpp](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/code/quick_sort.cpp)

```
/* Summary: 快速排序（Quick Sort）
* Author: Amusi
* Date:   2018-07-28
*
* Reference: 
*   https://en.wikipedia.org/wiki/Quicksort
*	
* 快速排序（quick sort）：通过一趟排序将待排列表分隔成独立的两部分，其中一部分的所有元素均比另一部分的所有元素小，则可分别对这两部分继续重复进行此操作，以达到整个序列有序。（这个过程，我们可以使用递归快速实现）
*
*/

#include <iostream>

// 快速排序函数（递归法）
namespace alg{
	template<typename T>
	static void QuickSort(T list[], int start, int end)
	{
		int i = start;
		int j = end;
		// 结束排序（左右两索引值见面，即相等，或者左索引>右索引）
		if (i >= j)
			return;
		// 保存首个数值（以首个数值作为基准）
		// 这个位置很重要，一定要在if i >= j判断语句之后，否则就索引溢出了
		T pivot = list[i];

		// 一次排序，i和j的值不断的靠拢，然后最终停止，结束一次排序
		while (i < j){
			// 一层循环实现从左边起大于基准的值替换基准的位置，右边起小于基准的值位置替换从左起大于基准值的索引
			//（从右往左）和最右边的比较，如果 >= pivot, 即满足要求，不需要交换，然后j - 1，慢慢左移，即拿基准值与前一个值比较; 如果值<pivot，那么就交换位置
			while (i < j && pivot <= list[j])
				--j;
			list[i] = list[j];
			// 交换位置后，（从左往右）然后在和最左边的值开始比较，如果 <= pivot, 然后i + 1，慢慢的和后一个值比较; 如果值>pivot，那么就交换位置
			while (i < j && pivot >= list[i])
				++i;
			list[j] = list[i];
		}
		// 列表中索引i的位置为基准值，i左边序列都是小于基准值的，i右边序列都是大于基准值的，当前基准值的索引为i，之后不变
		list[i] = pivot;
		// 左边排序
		QuickSort(list, start, i-1);
		// 右边排序
		QuickSort(list, i+1, end);
	}
}

using namespace std;
using namespace alg;


int main()
{
	int a[8] = { 5, 2, 5, 7, 1, -3, 99, 56 };
	QuickSort<int>(a, 0, sizeof(a)/sizeof(a[0]) - 1);
	for (auto e : a)
		std::cout << e << " ";

	return 0;
}
```

[quick_sort.py](https://github.com/amusi/coding-note/blob/master/Data%20Structures%20and%20Algorithms/sort/code/quick_sort.py)

```python
''' Summary: 快速排序（Quick Sort）
* Author: Amusi
* Date:   208-07-28
*
* Reference: 
*   https://en.wikipedia.org/wiki/Quicksort
*   https://www.cnblogs.com/wujingqiao/articles/8961890.html
*	https://github.com/apachecn/LeetCode/blob/master/src/py3.x/sort/QuickSort.py
*   快速排序（quick sort）：通过一趟排序将待排列表分隔成独立的两部分，其中一部分的所有元素均比另一部分的所有元素小，则可分别对这两部分继续重复进行此操作，以达到整个序列有序。（这个过程，我们可以使用递归快速实现）
*
'''

def QuickSort(array, start, end):
    lengths = len(array)
    i = start
    j = end
    # 结束排序（左右两索引值见面，即相等，或者左索引>右索引）
    if i >= j:
        return	# 返回空即可
    # 保存首个数值（以首个数值作为基准）
	# 这个位置很重要，一定要在if i>=j判断语句之后，否则就索引溢出了
    pivot = array[i]
    # 一次排序，i和j的值不断的靠拢，然后最终停止，结束一次排序
    while i < j:
        # （从右往左）和最右边的比较，如果>=pivot,即满足要求，不需要交换，然后j-1，慢慢左移，即拿基准值与前一个值比较; 如果值<pivot，那么就交换位置
        while i < j and pivot <= array[j]:
            # print(pivot, array[j], '*' * 30)
            j -= 1
        array[i] = array[j]
        # 交换位置后，然后在和最左边的值开始比较，如果<=pivot,然后i+1，慢慢的和后一个值比较;如果值>pivot，那么就交换位置
        while i < j and pivot >= array[i]:
            # print(pivot, array[i], '*' * 30)
            i += 1
        array[j] = array[i]
    # 列表中索引i的位置为基准值，i左边序列都是小于基准值的，i右边序列都是大于基准值的，当前基准值的索引为i，之后不变
    array[i] = pivot
    # 左边排序
    QuickSort(array, start, i-1)
    # 右边排序
    QuickSort(array, i+1, end)
		
    #return array

if __name__ == "__main__":
    array = [1,3,8,5,2,10,7,16,7,4,5]
    print("Original array: ", array)
    #array = QuickSort(array, 0, len(array)-1)
	# 因为python中的list对象是可变对象，所以在函数做"形参"时，是相当于按引用传递
	# 所以不写成返回值的形式，也是OK的
    QuickSort(array, 0, len(array)-1)
    print("QuickSort: ", array)
```

## 查找

- [ ] TODO

### 二分查找

- [ ] TODO

### lower_bound

- [ ] TODO

### upper_bound

- [ ] TODO

## 分治与递归

- [ ] TODO

### 逆序对数

- [ ] TODO

### 大数相加

- [ ] TODO

### 大数相乘

- [ ] TODO

## 贪婪算法

- [ ] TODO

## 动态规划

### 背包问题

- [ ] TODO

### 找零钱问题

- [ ] TODO

### 最长公共子序列（LCS） 

- [ ] TODO

## 字符串匹配算法

### KMP算法

- [ ] TODO

### BM算法

- [ ] TODO

### Sunday算法

- [ ] TODO

## 线性表

### 数组

- [ ] TODO

### 栈

- [ ] TODO

### 队列

- [ ] TODO

### 链表

- [ ] TODO

## 二叉树

### 二叉排序树/二叉查找树BST

- [ ] TODO

### 平衡二叉树

- [ ] TODO

### 求二叉树的最大高度

- [ ] TODO

### 二叉树的前序遍历

- [ ] TODO

### 二叉树打印出最右侧的节点

- [ ] TODO

### 非递归中序遍历二叉树

- [ ] TODO

### 求二叉树深度和宽度

- [ ] TODO

## 链表

### 找到链表倒数第k个结点

- [ ] TODO

### 如何判断单链表中是否有环？

- [ ] TODO

### 翻转链表

- [ ] TODO

### 手写双向链表

- [ ] TODO

## 堆

### 构建堆的复杂度

- [ ] TODO

### 堆找出第k大元素的复杂度 

- [ ] TODO

## 打印螺旋矩阵

- [ ] TODO

## 找最小字串

- [ ] TODO

## 2-sum、3-sum和4-sum问题

N-sum就是从序列中找出N个数，使得N个数之和等于指定数值的问题。

**2-sum**

2-sum就是从序列中找出2个数，使得2个数之和等于0的问题，即a+b=sum。

下面的例子是规定指定数值为0：

```cpp
int sum_2()
{
	int res = 0;
	int n = data.size();
	for(int i=0; i<n-1; i++)
	{
		for(int j=i+1; j<n; j++)
		{
			if(data[i] + data[j] == 0)
			{
				res ++;
			}
		}
	}
	return res;
}

```

上述算法的由于包含了两层循环，因此时间复杂度为O(N^2)。

观察发现，上述算法时间主要花费在数据比对，为此可以考虑使用二分查找来减少数据比对时间，要想使用二分查找，首先应该对数据进行排序，在此使用归并排序或者快速排序对数组进行升序排列。排序所花时间为O(NlogN)，排序之后数据查找只需要O(logN)的时间，但是总共需要查找N次，为此改进后算法的时间复杂度为O(NlogN)。

```cpp
int cal_sum_2()
{
	int res = 0;
	for(int i=0; i<data.size(); i++)
	{
		int j = binary_search(-data[i]);
		if(j > i)	
		res++;
	}
	return res;
}

```

**3-sum**

上述2-sum的解题思路适用于3-sum及4-sum问题，如求解a+b+c=0，可将其转换为求解a+b=-c，此就为2-sum问题。

为此将2-sum，3-sum，4-sum的求解方法以及相应的优化方法实现在如下所示的sum类中。

sum.h

```cpp
#ifndef SUM_H
#define SUM_H
#include <vector>
using std::vector;
class sum
{
private:
	vector<int> data;
public:
	sum(){};
	sum(const vector<int>& a);
	~sum(){};
	int cal_sum_2() const;
	int cal_sum_3() const;
	int cal_sum_4() const;
	int cal_sum_2_update() const;
	int cal_sum_3_update() const;
	int cal_sum_3_update2() const;
	int cal_sum_4_update() const;
	void sort(int low, int high);
	void print() const;
	friend int find(const sum& s, int target); 
};
#endif

```

sum.cpp

```cpp
#include "Sum.h"
#include <iostream>
using namespace std;
sum::sum(const vector<int>& a)
{
	data = a;
}
void sum::sort(int low, int high)
{
	if(low >= high)
		return;
	int mid = (low+high)/2;
	sort(low,mid);
	sort(mid+1,high);
	vector<int> temp;
	int l = low;
	int h = mid+1;
	while(l<=mid && h <=high)
	{
		if(data[l] > data[h])
			temp.push_back(data[h++]);
		else
			temp.push_back(data[l++]);
	}
	while(l<=mid)
		temp.push_back(data[l++]);
	while(h<=high)
		temp.push_back(data[h++]);
	for(int i=low; i<=high; i++)
	{
		data[i] = temp[i-low];
	}
}
void sum::print() const
{
	for(int i=0; i<data.size(); i++)
	{
		cout<<data[i]<<" ";
	}
	cout<<endl;
}
int find(const sum& s, int target)
{
	int low = 0;
	int high = s.data.size()-1;
	while(low <= high)
	{
		int mid = (low + high)/2;
		if(s.data[mid] < target)
		{
			low = mid+1;
		}
		else if(s.data[mid] > target)
		{
			high = mid - 1;
		}
		else
		{
			return mid;
		}
	}
	return -1;
}
int sum::cal_sum_2() const
{
	int res = 0;
	for(int i=0; i<data.size(); i++)
	{
		int j = find(*this, -data[i]);
		if(j > i)	
			res++;
	}
	return res;
}
int sum::cal_sum_3() const
{
	int res = 0;
	for(int i=0; i<data.size(); i++)
	{
		for(int j=i+1; j<data.size(); j++)
		{
			for(int p=j+1;p<data.size();p++)
			{
				if(data[i] + data[j] + data[p] == 0)
					res++;
			}
		}
	}
	return res;
}
int sum::cal_sum_4() const
{
	int res = 0;
	for(int i=0; i<data.size(); i++)
	{
		for(int j=i+1; j<data.size(); j++)
		{
			for(int p=j+1; p<data.size(); p++)
			{
				for(int q=p+1; q<data.size(); q++)
				{
					if(data[i]+data[j]+data[p]+data[q] == 0)
						res++;
				}
			}
		}
	}
	return res;
}
int sum::cal_sum_2_update() const
{
	int res = 0;
	for(int i=0,j=data.size()-1; i<j; )
	{
		if(data[i] + data[j] > 0)
			j--;
		else if(data[i] + data[j] < 0)
			i++;
		else
		{
			res++;
			j--;
			i++;
		}
	}
	return res;
}
int sum::cal_sum_3_update() const
{
	int res = 0;
	for(int i=0; i<data.size(); i++)
	{
		for(int j=i+1; j<data.size(); j++)
		{
			if(find(*this, -data[i] - data[j]) > j)
				res ++;
		}
	}
	return res;
}
int sum::cal_sum_3_update2() const
{
	int res = 0;
	for(int i=0; i<data.size(); i++)
	{
		int j=i+1;
		int p=data.size()-1;
		while(j<p)
		{
			if (data[j] + data[p] < -data[i])
				j++;
			else if(data[j] + data[p] > -data[i])
				p--;
			else
			{
				res++;
				j++;
				p--;
			}
		}
	}
	return res;
}
int sum::cal_sum_4_update() const
{
	int res = 0;
	for(int i=0; i<data.size(); i++)
	{
		for(int j=i+1; j<data.size(); j++)
		{
			for(int p=j+1; p<data.size(); p++)
			{
				if(find(*this, -data[i]-data[j]-data[p])>p)
					res++;
			}
		}
	}
	return res;
}

```

test.cpp

```cpp
#include "Sum.h"
#include <iostream>
#include <fstream>
#include <vector>
using namespace std;
void main()
{
	ifstream in("1Kints.txt");
	vector<int> a;
	while(!in.eof())
	{
		int temp;
		in>>temp;
		a.push_back(temp);
	}
	sum s(a);
	s.sort(0,a.size()-1);
	s.print();
	cout<<"s.cal_sum_2() = "<<s.cal_sum_2()<<endl;
	cout<<"s.cal_sum_2_update() = "<<s.cal_sum_2_update()<<endl;
	cout<<"s.cal_sum_3() = "<<s.cal_sum_3()<<endl;
	cout<<"s.cal_sum_3_update() = "<<s.cal_sum_3_update()<<endl;
	cout<<"s.cal_sum_3_update()2 = "<<s.cal_sum_3_update2()<<endl;
	cout<<"s.cal_sum_4() = "<<s.cal_sum_4()<<endl;
	cout<<"s.cal_sum_4_update() = "<<s.cal_sum_4_update()<<endl;
}

```

**参考资料**

- [剖析3-sum问题(Three sum)](https://blog.csdn.net/shaya118/article/details/40755551)
- [2-sum, 3-sum, 4-sum问题分析](http://shmilyaw-hotmail-com.iteye.com/blog/2085129)

## 无序数组a，b 归并排序成有序数组c

TODO

- [ ] ## 将256*256二维数组逆时针旋转90°

- [ ] TODO

## 二分查找

- [ ] TODO

## 分治与递归：逆序对数、大数相加、大数相乘

## 动态规划：背包问题、找零钱问题和最长公共子序列（LCS）

- [ ] TODO

## 青蛙跳台阶

- [ ] TODO

## BFS和DFS解决最短路径

- [ ] TODO

## DFS和BFS的区别（优缺点）

深度优先搜索算法（Depth-First-Search，DFS）是一种利用递归实现的搜索算法。简单来说，其搜索过程和"不撞南墙不回头"类似。

广度优先搜索算法（Breadth-First-Search，BFS）是一种利用队列实现的搜索算法。简单来说，其搜索过程和"湖面丢进一块石头激起层层涟漪"类似。

BFS 的重点在于队列，而 DFS 的重点在于递归。这是它们的本质区别。

**应用方向**

BFS 常用于找单一的最短路线，它的特点是 "搜到就是最优解"，而 DFS 用于找所有解的问题，它的空间效率高，而且找到的不一定是最优解，必须记录并完成整个搜索，故一般情况下，深搜需要非常高效的剪枝（剪枝的概念请百度）。

**参考资料**

- [一文读懂 BFS 和 DFS 区别](https://www.sohu.com/a/201679198_479559)

## 数组的最大区间和

- [ ] TODO

## 迪杰斯特拉 (Dijkstra) 算法

- [ ] TODO

## 两个栈实现一个队列

- [ ] TODO

​	- Coding：单例模式实现（2次） 

 	- Coding：stoi函数 

 	- Coding：二叉树对称判断（不用额外空间） 

 	- Coding：返回数组中和最大的子串 

 	- Coding：链表局部反转，每两个结点调换下位置（2次） 

 	- Coding：输入一个数组，取一些数出来，使和最大，约束是不能取相邻的元素，有负数，有小数 

 	- Coding：链表反转 

 	- Coding：swap函数 

 	- Coding：输入数组，将正数排到前面，负数在后面 

 	- Coding：设计实现Hashmap 

 	- Coding：求二叉树中节点的最远距离（3次）  

 	- Coding：找数组中位数 

 	- Coding：给一个点的集合和一个值K，把在以k为半径的区域内存在其他点的点列表输出 

 	- Coding：给一个数组，随机等概率删除数组中的一个数，要求高效 

 	- Coding：写个String类，把能想到的构造函数都写出来 

 	- Coding：atoi函数 

 	- Coding：给一个图，给两个结点，求两个结点之间的最短路径 

 	- Coding：单链表，删除值为k的节点 

 	- Coding：二叉树前序遍历 

 	- Coding：给一个上线时间段记录数组，和开始，结束时间，输出所有这段时间内的上下线记录 

 	- Coding：大小端，写个程序判断 

 	- Coding：两个有序链表merge 

 	- Coding：二分查找，有重复，findlast 

 	- Coding：x的y次方 

 	- Coding：链表倒数第k个节点 

 	- Coding：分数转化成小数，循环部分用括号包起来 

 	- Coding：输入一些时间段，输出最大重合数 

 	- Coding：hash数据结构设计 

 	- Coding：n个点的数组，按x轴排序 

 	- Coding：n个点的数组，两个同行或列的点可以移除一个，使最后图中节点最少，返回移除点的索引序列 

 	- Coding：链表尾结点插入头部，操作k次返回 

 	- Coding：给一个数组，能不能分成两个数组，它们平均值相等，能的话返回两个数组

## TODO

## 参考资料

# 参考

**[1]（推荐）**[《大话数据结构》](https://book.douban.com/subject/6424904/)

**[2]（推荐）**[十大经典排序算法（动图演示）](https://www.cnblogs.com/onepixel/p/7674659.html)

**[3]（推荐）**[轻松搞定十大排序算法(C++版)](https://blog.csdn.net/opooc/article/details/80994353)

**[4]（推荐）**[从头说12种排序算法：原理、图解、动画视频演示、代码以及笔试面试题目中的应用](https://blog.csdn.net/han_xiaoyang/article/details/12163251)

**[5]（推荐）**[排序算法时间复杂度、空间复杂度、稳定性比较](https://blog.csdn.net/yushiyi6453/article/details/76407640)

**[6]（推荐）**[十大排序算法和七大查找算法总结（原理讲解和Python代码实现）---（一）排序算法篇](https://www.cnblogs.com/wujingqiao/p/8961890.html)

**[7]** [常见排序算法C++总结](https://www.cnblogs.com/zyb428/p/5673738.html)

**[8]** [十大经典排序算法（JavaScript版）](http://web.jobbole.com/87968/)

**[9]** [八大排序算法总结（JAVA版）](http://www.runoob.com/w3cnote/sort-algorithm-summary.html)

**[10]** [C++代码](https://github.com/xtaci/algorithms/blob/master/include/selection_sort.h)

- [八大排序算法时间空间复杂度分析](https://www.nowcoder.com/discuss/200097)




