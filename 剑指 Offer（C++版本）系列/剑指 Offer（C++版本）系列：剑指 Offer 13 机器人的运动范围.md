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
- [剑指 Offer（C++版本）系列：剑指 Offer 12 矩阵中的路径](https://blog.csdn.net/TeFuirnever/article/details/118711939)
- 剑指 Offer（C++版本）系列：剑指 Offer 13 机器人的运动范围

## 1、题干
```

机器人的运动范围

地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？

 

示例 1：

输入：m = 2, n = 3, k = 1
输出：3
示例 2：

输入：m = 3, n = 1, k = 0
输出：1
提示：

1 <= n,m <= 100
0 <= k <= 20
通过次数145,986提交次数278,894



```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210714213042457.png)




## 2、深度优先搜索
深度优先搜索： 可以理解为暴力法遍历矩阵中所有字符串可能性。

算法流程：
- 递归参数： 当前元素在矩阵中的行索引 m 和列索引 n ，索引的数位 k ，以及计数索引 x, y 。
- 终止条件： 
	- 返回 return；当 (1) 行索引或者列索引越界 (2) 数位和超出目标值 k (3) 当前元素已被访问过。
- 递归过程：
	- 标记当前单元格 ：将索引 (x, y) 对应的二维向量 visited 中设置为1，代表此单元格已被访问过。
	- 搜索下一单元格： 计算当前元素的 上、下、左、右 四个方向元素的数位和，并开启下层递归 。


```cpp
//面试题13. 机器人的运动范围
//标准做法
class Solution {
public:
	int count = 0;
	int movingCount(int m, int n, int k) {
		if (k == 0) return 1;
		vector<vector<int>> visited(m, vector<int>(n));
		dfs(visited, 0, 0, m, n, k);
		return count;
	}
	void dfs(vector<vector<int>>& visited, int x, int y, int& m, int& n, int k)
	{
		if (x >= m || x < 0 || y >= n || y<0 || (x / 10 + x % 10 + y / 10 + y % 10)>k || visited[x][y] == 1) 
			return;
		++count;
		visited[x][y] = 1;
		int dx[4] = { -1, 0, 1, 0 }, dy[4] = { 0, 1, 0, -1 };
		for (int q = 0; q<4; ++q){
			int i = x + dx[q], j = y + dy[q];
			dfs(visited, i, j, m, n, k);
		}
		/*dfs(visited, x + 1, y, m, n, k);
		dfs(visited, x, y + 1, m, n, k);
		dfs(visited, x - 1, y, m, n, k);
		dfs(visited, x, y - 1, m, n, k);*/
	}
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021071421454660.png)




![在这里插入图片描述](https://img-blog.csdnimg.cn/2021071421561462.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RlRnVpcm5ldmVy,size_16,color_FFFFFF,t_70#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210714215624141.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RlRnVpcm5ldmVy,size_16,color_FFFFFF,t_70#pic_center)







## 4、复杂度
```cpp
/*
时间复杂度 O(MN) ： 最差情况下，机器人遍历矩阵所有单元格，此时时间复杂度为 O(MN) 。
空间复杂度 O(MN) ： 最差情况下，visited 内存储矩阵所有单元格的索引，使用 O(MN) 的额外空间。
*/
```

——————————————————————————————————————


本文由 leetcode、牛客、公众哈哦、知乎共同支持！

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210703094425459.png)

[https://leetcode-cn.com/u/tefuirnever/](https://leetcode-cn.com/u/tefuirnever/)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210703094436257.png)

[https://blog.nowcoder.net/wsguanxl](https://blog.nowcoder.net/wsguanxl)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210703094516804.png)

[https://mp.weixin.qq.com/s/bDwxwQfZytIx4mAn8eK20Q](https://mp.weixin.qq.com/s/bDwxwQfZytIx4mAn8eK20Q)

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021070309445723.png)

[https://www.zhihu.com/people/tefuirnever_-.-](https://www.zhihu.com/people/tefuirnever_-.-)


