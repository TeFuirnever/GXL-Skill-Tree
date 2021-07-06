@[toc]

## 同步GitHub在此 👉 [https://github.com/TeFuirnever/GXL-Skill-Tree](https://github.com/TeFuirnever/GXL-Skill-Tree)

- [剑指 Offer（C++版本）系列：总目录和一些提高效率的说明](https://tefuirnever.blog.csdn.net/article/details/118423883)
- [剑指 Offer（C++版本）系列：剑指 Offer 03 数组中重复的数字](https://tefuirnever.blog.csdn.net/article/details/118445391)
- [剑指 Offer（C++版本）系列：剑指 Offer 04 二维数组中的查找](https://tefuirnever.blog.csdn.net/article/details/118467105)
- [剑指 Offer（C++版本）系列：剑指 Offer 05 替换空格](https://tefuirnever.blog.csdn.net/article/details/118498159)
- [剑指 Offer（C++版本）系列：剑指 Offer 06 从尾到头打印链表](https://tefuirnever.blog.csdn.net/article/details/118529012)

## 1、题干
```

从尾到头打印链表

输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

 

示例 1：

输入：head = [1,3,2]
输出：[2,3,1]
 

限制：

0 <= 链表长度 <= 10000

通过次数242,193提交次数322,163


```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210706202858264.png)



## 2、辅助栈法
注意到题目要求是倒序输出节点值，这种先入后出的需求可以借助栈来实现。

算法流程：
1. 初始化：一个数组，一个栈
2. 入栈： 遍历整个链表，将各节点值 push 入栈。
3. 出栈： 将各节点值 pop 出栈，存储于数组并返回。
4. 返回答案数组。


```cpp
//面试题06.从尾到头打印链表
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> reversePrint(ListNode* head) {
        stack<int> stk;
        vector<int> res;
        while(head)
        {
            stk.push(head->val);
            head=head->next;
        }
        while(!stk.empty())
        {
            res.push_back(stk.top());
            stk.pop();
        }
        return res;
    }
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210706205814216.png)

```cpp
/*
时间复杂度：O(n)。正向遍历一遍链表，然后从栈弹出全部节点，等于又反向遍历一遍链表。
空间复杂度：O(n)。额外使用一个栈存储链表中的每个节点。
*/
```

## 3、数组模拟辅助栈法

可以通过数组实现栈的功能。

算法流程：
1. 初始化：一个数组，模拟栈
2. 入栈： 遍历整个链表，将各节点值 push_back 入数组。
3. 返回反向答案数组。


```cpp
//面试题06.从尾到头打印链表
//标准做法
/**
* Definition for singly-linked list.
* struct ListNode {
*     int val;
*     ListNode *next;
*     ListNode(int x) : val(x), next(NULL) {}
* };
*/
class Solution {
public:
	vector<int> reversePrint(ListNode* head) {
		vector<int> res;
		while (head)
		{
			res.push_back(head->val);
			head = head->next;
		}
		return vector<int>(res.rbegin(), res.rend());
	}
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210706212043658.png)


![在这里插入图片描述](https://img-blog.csdnimg.cn/20210706213022375.png)



## 4、复杂度
```cpp
/*
时间复杂度：O(n)。正向遍历一遍链表。
空间复杂度：O(n)。额外使用一个数组存储链表中的每个节点。
*/
```

——————————————————————————————————————

- [剑指 Offer（C++版本）系列：总目录和一些提高效率的说明](https://tefuirnever.blog.csdn.net/article/details/118423883)
- [剑指 Offer（C++版本）系列：剑指 Offer 03 数组中重复的数字](https://tefuirnever.blog.csdn.net/article/details/118445391)
- [剑指 Offer（C++版本）系列：剑指 Offer 04 二维数组中的查找](https://tefuirnever.blog.csdn.net/article/details/118467105)
- [剑指 Offer（C++版本）系列：剑指 Offer 05 替换空格](https://tefuirnever.blog.csdn.net/article/details/118498159)
- [剑指 Offer（C++版本）系列：剑指 Offer 06 从尾到头打印链表](https://tefuirnever.blog.csdn.net/article/details/118529012)

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


