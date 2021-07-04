@[toc]

## 同步GitHub在此 👉 [https://github.com/TeFuirnever/GXL-Skill-Tree](https://github.com/TeFuirnever/GXL-Skill-Tree)

- [剑指 Offer（C++版本）系列：总目录和一些提高效率的说明](https://tefuirnever.blog.csdn.net/article/details/118423883)
- [剑指 Offer（C++版本）系列：剑指 Offer 03 数组中重复的数字](https://tefuirnever.blog.csdn.net/article/details/118445391)
- [剑指 Offer（C++版本）系列：剑指 Offer 04 二维数组中的查找](https://tefuirnever.blog.csdn.net/article/details/118467105)

## 1、题干
```

二维数组中的查找

在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。


示例:

现有矩阵 matrix 如下：

[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
给定 target = 5，返回 true。

给定 target = 20，返回 false。


限制：

0 <= n <= 1000

0 <= m <= 1000

注意：本题与主站 240 题相同：https://leetcode-cn.com/problems/search-a-2d-matrix-ii/

通过次数211,829提交次数525,418

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210704204915785.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210704204941314.png)


## 2、二分搜索树
注意题干，【每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序】，那么说明数组中的数据是具有一定规律的。



算法流程：
1. 若矩阵 matrix 为空，返回 false；
2. 从矩阵 matrix 左下角元素（索引设为 (i, j) ）开始遍历，并与目标值对比：
	1. 当 matrix[i][j] == target 时，返回 true ，代表找到目标值。
	2. 当 matrix[i][j] > target 时，执行 i-- ，即消去第 i 行元素；
	3. 当 matrix[i][j] < target 时，执行 j++ ，即消去第 j 列元素；
3. 若行索引或列索引越界，则代表矩阵中无目标值，返回 false。
	1. 每轮 i 或 j 移动后，相当于生成了“消去一行（列）的新矩阵”， 索引(i, j) 默认指向新矩阵的左下角元素（标志数）。


```cpp
//面试题04.二维数组中的查找
//标准做法
class Solution {
public:
	bool findNumberIn2DArray(vector<vector<int>>& matrix, int target) {
		if (matrix.empty() || matrix[0].empty()) return false;
		int i = matrix.size()-1, j = 0;
		while (i >= 0 &&  j < matrix[0].size())
		{
			if (matrix[i][j] == target) return true;
			if (matrix[i][j]>target) i--;
			else j++;
		}
		return false;
	}
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210704210749305.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210704212531679.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210704212531758.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210704212531794.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210704212531697.png)

## 4、复杂度
```cpp
/*
时间复杂度：O(n+m)。访问到的下标的行最多增加 n 次，列最多减少 m 次，因此循环体最多执行 n + m 次。
空间复杂度：O(1)
*/
```

——————————————————————————————————————

- [剑指 Offer（C++版本）系列：总目录和一些提高效率的说明](https://tefuirnever.blog.csdn.net/article/details/118423883)
- [剑指 Offer（C++版本）系列：剑指 Offer 03 数组中重复的数字](https://tefuirnever.blog.csdn.net/article/details/118445391)
- [剑指 Offer（C++版本）系列：剑指 Offer 04 二维数组中的查找](https://tefuirnever.blog.csdn.net/article/details/118467105)

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


