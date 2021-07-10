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

## 1、题干
```

斐波那契数列

写一个函数，输入 n ，求斐波那契（Fibonacci）数列的第 n 项（即 F(N)）。斐波那契数列的定义如下：

F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), 其中 N > 1.
斐波那契数列由 0 和 1 开始，之后的斐波那契数就是由之前的两数相加而得出。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

 

示例 1：

输入：n = 2
输出：1
示例 2：

输入：n = 5
输出：5
 

提示：

0 <= n <= 100
通过次数190,890提交次数552,092


```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210710212612437.png)



## 2、递归法

算法流程：
- 转移方程：即对应数列定义 f(n + 1) = f(n) + f(n - 1)；
- 初始状态： 即初始化前两个数字；
- 返回值： 即斐波那契数列的第 n 个数字。

```cpp
//面试题10- I. 斐波那契数列
//标准做法
class Solution {
public:
	int fib(int n) {
		int a = 0, b = 1, c = 0;
		for (int i = 0; i < n; ++i)
		{
			a = b, b = c;
			c = (a + b) % 1000000007;
		}
		return c;
	}
};

//long long 更佳
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210710212940208.png)


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210710213935616.png)



## 4、复杂度
```cpp
/*
时间复杂度O(n)， 迭代n次
空间复杂度O(1)
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


