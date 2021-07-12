@[toc]

## 同步GitHub在此 👉 [https://github.com/TeFuirnever/GXL-Skill-Tree](https://github.com/TeFuirnever/GXL-Skill-Tree)

- [剑指 Offer（C++版本）系列：总目录和一些提高效率的说明](https://tefuirnever.blog.csdn.net/article/details/118423883)
- [剑指 Offer（C++版本）系列：剑指 Offer 03 数组中重复的数字](https://tefuirnever.blog.csdn.net/article/details/118445391)
- [剑指 Offer（C++版本）系列：剑指 Offer 04 二维数组中的查找](https://tefuirnever.blog.csdn.net/article/details/118467105)
- [剑指 Offer（C++版本）系列：剑指 Offer 05 替换空格](https://tefuirnever.blog.csdn.net/article/details/118498159)
- [剑指 Offer（C++版本）系列：剑指 Offer 06 从尾到头打印链表](https://tefuirnever.blog.csdn.net/article/details/118529012)
- [剑指 Offer（C++版本）系列：剑指 Offer 07 重建二叉树](https://tefuirnever.blog.csdn.net/article/details/118557615)
- [剑指 Offer（C++版本）系列：剑指 Offer 09 用两个栈实现队列](https://tefuirnever.blog.csdn.net/article/details/118614718)
- [剑指 Offer（C++版本）系列：剑指 Offer 10- I 斐波那契数列](https://tefuirnever.blog.csdn.net/article/details/118640975)
- [剑指 Offer（C++版本）系列：剑指 Offer 10- II 青蛙跳台阶问题](https://tefuirnever.blog.csdn.net/article/details/118661038)
- [剑指 Offer（C++版本）系列：剑指 Offer 11 旋转数组的最小数字](https://tefuirnever.blog.csdn.net/article/details/118684466)

## 1、题干
```

旋转数组的最小数字

把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一个旋转，该数组的最小值为1。  

示例 1：

输入：[3,4,5,1,2]
输出：1
示例 2：

输入：[2,2,2,0,1]
输出：0

通过次数215,217提交次数436,094



```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210712213651142.png)



## 2、二分查找法
算法流程：
- 初始化： 声明 left, right 双指针，分别指向 numbers 数组左右两端；
- 二分查找： 设 mid = (left + right) >> 1 为中点可分为以下三种情况：
	1. 当 numbers[mid] > numbers[right] 时： mid 一定在 左排序数组 中，即旋转点 x 一定在 [mid + 1, right] 闭区间内，因此执行 left = mid + 1（递增排序时，numbers[mid] < numbers[right] 不符合）；
	2. 当 numbers[mid] < numbers[right] 时： mid 一定在 右排序数组 中，即旋转点 x 一定在 [left, mid] 闭区间内，因此执行 right = mid；
	3. 当 numbers[mid] == numbers[right] 时： 无法判断 mid 在 哪个排序数组 中，即无法判断旋转点 x 在 [left, mid] 还是 [mid + 1, right] 区间中。解决方案： 执行 right = right - 1 缩小判断范围。
- 返回值： 当 left == right 时跳出二分循环，并返回 旋转点的值 numbers[left] 即可。


```cpp
//面试题11. 旋转数组的最小数字
//标准做法
class Solution {
public:
	int minArray(vector<int>& numbers) {
		int size = numbers.size();
		int left = 0, right = size - 1;
		while (left<right)
		{
			int mid = (left + right) >> 1;
			if (numbers[mid]>numbers[right])
			{
				left = mid + 1;
			}
			else if (numbers[mid]<numbers[right])
			{
				right = mid;
			}
			else
			{
				right--;
			}
		}
		return numbers[left];
	}
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021071222011528.png)



![在这里插入图片描述](https://img-blog.csdnimg.cn/20210712221853688.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RlRnVpcm5ldmVy,size_16,color_FFFFFF,t_70#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210712221904407.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RlRnVpcm5ldmVy,size_16,color_FFFFFF,t_70#pic_center)





## 4、复杂度
```cpp
/*
时间复杂度 O(log2N) ： 在特例情况下（例如 [1,1,1,1]），会退化到 O(N)。
空间复杂度 O(1) ： left , right , mid 指针使用常数大小的额外空间。
*/
```

——————————————————————————————————————

- [剑指 Offer（C++版本）系列：总目录和一些提高效率的说明](https://tefuirnever.blog.csdn.net/article/details/118423883)
- [剑指 Offer（C++版本）系列：剑指 Offer 03 数组中重复的数字](https://tefuirnever.blog.csdn.net/article/details/118445391)
- [剑指 Offer（C++版本）系列：剑指 Offer 04 二维数组中的查找](https://tefuirnever.blog.csdn.net/article/details/118467105)
- [剑指 Offer（C++版本）系列：剑指 Offer 05 替换空格](https://tefuirnever.blog.csdn.net/article/details/118498159)
- [剑指 Offer（C++版本）系列：剑指 Offer 06 从尾到头打印链表](https://tefuirnever.blog.csdn.net/article/details/118529012)
- [剑指 Offer（C++版本）系列：剑指 Offer 07 重建二叉树](https://tefuirnever.blog.csdn.net/article/details/118557615)
- [剑指 Offer（C++版本）系列：剑指 Offer 09 用两个栈实现队列](https://tefuirnever.blog.csdn.net/article/details/118614718)
- [剑指 Offer（C++版本）系列：剑指 Offer 10- I 斐波那契数列](https://tefuirnever.blog.csdn.net/article/details/118640975)
- [剑指 Offer（C++版本）系列：剑指 Offer 10- II 青蛙跳台阶问题](https://tefuirnever.blog.csdn.net/article/details/118661038)
- [剑指 Offer（C++版本）系列：剑指 Offer 11 旋转数组的最小数字](https://tefuirnever.blog.csdn.net/article/details/118684466)

—————————————————————————————————————

本文由 leetcode、牛客、公众哈哦、知乎共同支持！

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210703094425459.png)

[https://leetcode-cn.com/u/tefuirnever/](https://leetcode-cn.com/u/tefuirnever/)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210703094436257.png)

[https://blog.nowcoder.net/wsguanxl](https://blog.nowcoder.net/wsguanxl)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210703094516804.png)

[https://mp.weixin.qq.com/s/bDwxwQfZytIx4mAn8eK20Q](https://mp.weixin.qq.com/s/bDwxwQfZytIx4mAn8eK20Q)

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021070309445723.png)

[https://www.zhihu.com/people/tefuirnever_-.-](https://www.zhihu.com/people/tefuirnever_-.-)


