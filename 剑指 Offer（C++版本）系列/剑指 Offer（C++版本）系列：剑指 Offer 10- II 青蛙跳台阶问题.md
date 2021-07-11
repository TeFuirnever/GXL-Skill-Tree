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

## 1、题干
```

青蛙跳台阶问题

一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 n 级的台阶总共有多少种跳法。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

示例 1：

输入：n = 2
输出：2
示例 2：

输入：n = 7
输出：21
示例 3：

输入：n = 0
输出：1
提示：

0 <= n <= 100
注意：本题与主站 70 题相同：https://leetcode-cn.com/problems/climbing-stairs/

 

通过次数157,985提交次数361,363



```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210711221421614.png)



## 2、滑动窗口法

算法流程：
- 转移方程：即对应数列定义 f(n + 1) = f(n) + f(n - 1)；
- 初始状态： 即初始化前两个数字；与 [剑指 Offer（C++版本）系列：剑指 Offer 10- I 斐波那契数列](https://blog.csdn.net/TeFuirnever/article/details/118640975?spm=1001.2014.3001.5501) 等价，唯一的不同在于初始化：
	- 斐波那契数列问题： f(0)=0 , f(1)=1 , f(2)=0 ；
	- 青蛙跳台阶问题： f(0)=0 , f(1)=1 , f(2)=1 ；
- 返回值： 即斐波那契数列的第 n 个数字。

```cpp
//面试题10- II. 青蛙跳台阶问题
//标准做法
class Solution {
public:
	int numWays(int n) {
		int a = 0, b = 1, c = 1;
		for (int i = 0; i<n; ++i)
		{
			a = b; b = c;
			c = (a + b) % 1000000007;
		}
		return b;
	}
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210711222233722.png)



![在这里插入图片描述](https://img-blog.csdnimg.cn/20210711222705575.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RlRnVpcm5ldmVy,size_16,color_FFFFFF,t_70#pic_center)




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
- [剑指 Offer（C++版本）系列：剑指 Offer 10- II 青蛙跳台阶问题](https://tefuirnever.blog.csdn.net/article/details/118661038)

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


