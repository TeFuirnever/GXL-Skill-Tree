@[toc]

## 同步GitHub在此 👉 [https://github.com/TeFuirnever/GXL-Skill-Tree](https://github.com/TeFuirnever/GXL-Skill-Tree)

- [剑指 Offer（C++版本）系列：总目录和一些提高效率的说明](https://tefuirnever.blog.csdn.net/article/details/118423883)
- [剑指 Offer（C++版本）系列：剑指 Offer 03 数组中重复的数字](https://tefuirnever.blog.csdn.net/article/details/118445391)
- [剑指 Offer（C++版本）系列：剑指 Offer 04 二维数组中的查找](https://tefuirnever.blog.csdn.net/article/details/118467105)
- [剑指 Offer（C++版本）系列：剑指 Offer 05 替换空格](https://tefuirnever.blog.csdn.net/article/details/118498159)

## 1、题干
```

替换空格

请实现一个函数，把字符串 s 中的每个空格替换成"%20"。

 
示例 1：

输入：s = "We are happy."
输出："We%20are%20happy."
 

限制：

0 <= s 的长度 <= 10000

通过次数227,105提交次数297,856


```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210705204218776.png)


## 2、遍历添加
最应该想到的方法是，首先新建一个字符串，然后从头遍历原字符串，如果遇到满足要求的，修改即可，如果没遇到，保留下来。

算法流程：
1. 初始化一个字符串，记为 res ；
2. 遍历原字符串 s 中的每个字符 x ：
	1. 当 x 为空格时：向 res 后添加字符串 "%20" ；
	2. 当 x 不为空格时：向 res 后添加字符 x ；
3. 返回字符串 res 。


```cpp
//面试题05.替换空格
class Solution {
public:
	string replaceSpace(string s) {
		string res;
		for (auto x : s)
		{
			if (x == ' ') res += "%20";
			else res += x;
		}
		return res;
	}
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210705205232136.png)
```cpp
/*
时间复杂度：O(n)。遍历字符串 s 一遍。
空间复杂度：O(n)
*/
```

## 3、原地修改
需要注意的是，空间复杂度，由于新建一个答案字符串，所以空间复杂度不是常数。


算法流程：
1. 初始化：原字符串 s 的长度 oldl  ；
2. 统计空格数量：遍历 s ，遇空格则 s += "00"；
3. 重新初始化：原字符串 s 长度 newl ：添加完 "%20" 后的字符串长度；
4. 倒序遍历修改：i 指向字符串 s 尾部元素；
	1. 当 s[i] 为空格时：将字符串 newl 的元素分别修改为 "%20" ，每次修改后都需要移动 newl ；
	2. 当 s[i] 不为空格时：将字符串 newl 的元素修改为 c ；
5. 返回已修改的字符串 s ；


```cpp
//面试题05.替换空格
//标准做法
class Solution {
public:
	string replaceSpace(string s) {
		int oldl = s.length() - 1;
		for (int i = 0; i <= oldl; i++) {
			if (s[i] == ' ') {
				s += "00";
			}
		}
		int newl = s.length() - 1;
		if (newl <= oldl) {
			return s;
		}
		for (int i = oldl; i >= 0; i--) {
			char c = s[i];
			if (c == ' ') {
				s[newl--] = '0';
				s[newl--] = '2';
				s[newl--] = '%';
			}
			else {
				s[newl--] = c;
			}
		}
		return s;
	}
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210705210810726.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210705213111471.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210705213118679.png)



## 4、复杂度
```cpp
/*
时间复杂度：O(n)。遍历字符串 s 一遍。
空间复杂度：O(1)。由于是原地扩展 s 长度，因此使用 O(1)O(1) 额外空间。
*/
```

——————————————————————————————————————

- [剑指 Offer（C++版本）系列：总目录和一些提高效率的说明](https://tefuirnever.blog.csdn.net/article/details/118423883)
- [剑指 Offer（C++版本）系列：剑指 Offer 03 数组中重复的数字](https://tefuirnever.blog.csdn.net/article/details/118445391)
- [剑指 Offer（C++版本）系列：剑指 Offer 04 二维数组中的查找](https://tefuirnever.blog.csdn.net/article/details/118467105)
- [剑指 Offer（C++版本）系列：剑指 Offer 05 替换空格](https://tefuirnever.blog.csdn.net/article/details/118498159)

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


