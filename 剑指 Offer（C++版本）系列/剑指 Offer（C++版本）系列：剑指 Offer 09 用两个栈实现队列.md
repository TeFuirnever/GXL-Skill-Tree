@[toc]

## 同步GitHub在此 👉 [https://github.com/TeFuirnever/GXL-Skill-Tree](https://github.com/TeFuirnever/GXL-Skill-Tree)

- [剑指 Offer（C++版本）系列：总目录和一些提高效率的说明](https://tefuirnever.blog.csdn.net/article/details/118423883)
- [剑指 Offer（C++版本）系列：剑指 Offer 03 数组中重复的数字](https://tefuirnever.blog.csdn.net/article/details/118445391)
- [剑指 Offer（C++版本）系列：剑指 Offer 04 二维数组中的查找](https://tefuirnever.blog.csdn.net/article/details/118467105)
- [剑指 Offer（C++版本）系列：剑指 Offer 05 替换空格](https://tefuirnever.blog.csdn.net/article/details/118498159)
- [剑指 Offer（C++版本）系列：剑指 Offer 06 从尾到头打印链表](https://tefuirnever.blog.csdn.net/article/details/118529012)
- [剑指 Offer（C++版本）系列：剑指 Offer 07 重建二叉树](https://tefuirnever.blog.csdn.net/article/details/118557615)
- [剑指 Offer（C++版本）系列：剑指 Offer 09 用两个栈实现队列](https://tefuirnever.blog.csdn.net/article/details/118614718)

## 1、题干
```

用两个栈实现队列

用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )


示例 1：

输入：
["CQueue","appendTail","deleteHead","deleteHead"]
[[],[3],[],[]]
输出：[null,null,3,-1]
示例 2：

输入：
["CQueue","deleteHead","appendTail","appendTail","deleteHead","deleteHead"]
[[],[],[5],[2],[],[]]
输出：[null,-1,null,null,5,2]
提示：

1 <= values <= 10000
最多会对 appendTail、deleteHead 进行 10000 次调用
通过次数202,426提交次数280,577


```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210709210957876.png)


## 2、递归法
队列是先入先出，栈是先入后出。

算法流程：
1. 加入队尾 appendTail(int value) 函数： 把数字 value 加入栈 stk 即可；
2. 加入复制 copy(stack<int> &a, stack<int> &b) 函数，把栈 a 的元素复制到栈 b 中；
3. 删除队首 deleteHead() 函数：
	1. 当栈 stk 为空，即两个栈都为空，因此返回 -1 ；
	2. 把 stk 中所有元素 copy() 复制到 cache 中；
	3. 记录 cache 的栈顶元素，并删除该元素；
	4. 把 cache 中所有元素 copy() 复制到 stk 中；
	5. 直接返回被记录的栈顶元素。


```cpp
//面试题09. 用两个栈实现队列
//标准做法
class CQueue {
public:
	stack<int> stk, cache;
	CQueue() {

	}

	void appendTail(int value) {
		stk.push(value);
	}

	void copy(stack<int> &a, stack<int> &b) {
		while (a.size()) {
			b.push(a.top());
			a.pop();
		}
	}

	int deleteHead() {
		if (stk.empty())
		{
			return -1;
		}
		copy(stk, cache);
		int res = cache.top();
		cache.pop();
		copy(cache, stk);
		return res;
	}
};

/**
* Your CQueue object will be instantiated and called as such:
* CQueue* obj = new CQueue();
* obj->appendTail(value);
* int param_2 = obj->deleteHead();
*/
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021070921204796.png)


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210709220506203.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210709220516478.png)



## 4、复杂度
```cpp
/*
插入元素

时间复杂度：O(1)。
空间复杂度：O(n)。最差情况下，需要保存n个元素。

删除元素

时间复杂度：O(n)。
空间复杂度：O(n)。最差情况下，需要保存n个元素。
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


