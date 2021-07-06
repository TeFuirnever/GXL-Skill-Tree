@[toc]

## 同步GitHub在此 👉 [https://github.com/TeFuirnever/GXL-Skill-Tree](https://github.com/TeFuirnever/GXL-Skill-Tree)

- [剑指 Offer（C++版本）系列：总目录和一些提高效率的说明](https://tefuirnever.blog.csdn.net/article/details/118423883)
- [剑指 Offer（C++版本）系列：剑指 Offer 03 数组中重复的数字](https://tefuirnever.blog.csdn.net/article/details/118445391)
- [剑指 Offer（C++版本）系列：剑指 Offer 04 二维数组中的查找](https://tefuirnever.blog.csdn.net/article/details/118467105)
- [剑指 Offer（C++版本）系列：剑指 Offer 05 替换空格](https://tefuirnever.blog.csdn.net/article/details/118498159)

## 1、题干
```

找出数组中重复的数字。


在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。
数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。
请找出数组中任意一个重复的数字。

示例 1：

输入：
[2, 3, 1, 0, 2, 5, 3]
输出：2 或 3 
 

限制：

2 <= n <= 100000

通过次数330,298提交次数488,116

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210703213318503.png)

## 2、哈希表
根据目前已经学习过的数据结构，很容易想到哈希表，记录数组中的各个数字的次数。当查到哪个数字的次数不是1，那么一定有多个该数字，那么将该重复数字直接返回。

算法流程：
1. 初始化： 新建哈希表 map，记为 hash，第一个位置是数字，第二个位置是次数；
2. 遍历数组 nums 中的每个数字 nums[i] ：
	1. 将 nums[i] 添加至 hash 中；
	2. 当 nums[i] 在 hash 中的次数非 1，说明重复，直接返回 nums[i] ；
3. 返回 -1 ，找不到重复的数字，返回 -1 。

```cpp
//面试题03.数组中重复的数字
//map存储
class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
        map<int, int> hash;
        for(int i = 0; i < nums.size(); ++ i)
        {
            hash[nums[i]] ++ ;
            if(hash[nums[i]] != 1) return nums[i];
        }
        return -1;
    }
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210703214938104.png)

```cpp
//等效代码
class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
    	//unordered_map<int, int> hash;
        map<int, int> hash;
        //for(int i = 0; i < nums.size(); ++ i)
        for(int num : nums)
        {
            hash[num] ++ ;
            if(hash[num] != 1) return num;
        }
        return -1;
    }
};
```

## 3、原地置换
由于数组的长度是 n ，而数字也是 0 - n-1，因此可以使得索引与数组中该索引的数字相同，而同一个索引对应多个数字时必然重复了。

算法流程：
1. 遍历数组 nums 中的每个数字 nums[i] ：
	1. 将 nums[i] == nums[nums[i]]，说明该数字与该数字索引的数字相同；
	2. 当 nums[i] != nums[nums[i]]，可以交换使之符合 1.1 中情况；
2. 如果 nums[i] == i，说明交换有效果了，否则返回答案 nums[i] ；
3. 返回 -1 ，找不到重复的数字，返回 -1 

```cpp
//面试题03.数组中重复的数字
//标准做法
class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
        for(int i = 0; i < nums.size(); ++ i)
        {
            while(nums[i] != nums[nums[i]]) swap(nums[i], nums[nums[i]]);
            if(nums[i] != i) return nums[i];
        }
        return -1;
    }
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210703220535348.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210703222518295.jpg)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210703222542396.jpg)


## 4、复杂度
```cpp
/*
代码中尽管有一个两重循环，但每个数字最多只要交换两次就能找到属于它自己的位置，
因此总的时间复杂度是O（n）。
另外，所有的操作步骤都是在输入数组上进行的，不需要额外分配内存，因此空间复杂度为O（1）。
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


