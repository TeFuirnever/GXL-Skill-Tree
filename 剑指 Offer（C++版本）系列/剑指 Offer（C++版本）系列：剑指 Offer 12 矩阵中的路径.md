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
- 剑指 Offer（C++版本）系列：剑指 Offer 12 矩阵中的路径

## 1、题干
```

矩阵中的路径

给定一个 m x n 二维字符网格 board 和一个字符串单词 word 。如果 word 存在于网格中，返回 true ；否则，返回 false 。

单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中“相邻”单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。


例如，在下面的 3×4 的矩阵中包含单词 "ABCCED"（单词中的字母已标出）。


示例 1：

输入：board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
输出：true
示例 2：

输入：board = [["a","b"],["c","d"]], word = "abcd"
输出：false
 

提示：

1 <= board.length <= 200
1 <= board[i].length <= 200
board 和 word 仅由大小写英文字母组成
 

注意：本题与主站 79 题相同：https://leetcode-cn.com/problems/word-search/

通过次数138,752提交次数305,361



```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210713215248811.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210713215312385.png)




## 2、深度优先搜索
深度优先搜索： 可以理解为暴力法遍历矩阵中所有字符串可能性。即 DFS 通过递归，先朝一个方向搜到底，再回溯至上个节点，沿另一个方向搜索，以此类推，直到完成全部搜索或者停止。

剪枝： 在搜索中，遇到 这条路不可能成功 的情况，则应立即返回，放弃这个节点 。

算法流程：
- 递归参数： 当前字符在矩阵 board 中的行索引 i 和列索引 j ，当前目标字符（匹配的）在目标字符串 word 中的索引 k 。
- 终止条件：
	- 返回 false ： (1) 行索引或列索引越界 (2) 当前矩阵字符与目标字符不同；
	- 返回 true ： 当前目标字符（匹配的）在目标字符串 word 中的索引 k = len(word) - 1 ，即目标字符串 word 已全部匹配；
- 递归过程：
	- 标记访问过字符： 将 board[i][j] 修改为 '/' ，代表此元素已访问过，防止之后搜索时重复访问。
	- 搜索当前字符的下一单元格： 朝当前元素的 上、下、左、右 四个方向开启下层递归，并记录结果至布尔变量 res 。
	- 回溯当前字符： 将 board[i][j] 元素还原至初始值 。
- 返回值： 返回布尔量 res ，代表是否搜索到目标字符串。


```cpp
//面试题12. 矩阵中的路径
//标准做法
class Solution {
public:
    bool exist(vector<vector<char>>& board, string word) {
        for (int i = 0; i < board.size(); i++) {
            for (int j = 0; j < board[0].size(); j++) {
                if (dfs(board, word, i, j, 0))
                    return true;
            }
        }
        return false;
    }
    bool dfs(vector<vector<char>>& b, string& w, int i, int j, int k) {
        if (i >= b.size() || i < 0 || j >= b[0].size() || j < 0 || b[i][j] != w[k])
            return false;
        if (k == w.length() - 1)
            return true;
        char temp = b[i][j];
        b[i][j] = '/';
        bool res = dfs(b, w, i + 1, j, k + 1) || 
                   dfs(b, w, i - 1, j, k + 1) || 
                   dfs(b, w, i, j + 1, k + 1) || 
                   dfs(b, w, i, j - 1, k + 1);
		/*
		可以这么写，比较好：
		int dx[4] = {-1, 0, 1, 0}, dy[4] = {0, 1, 0, -1};
        for (int q = 0; q < 4; q ++ ) {
            int m = i + dx[q], n = j + dy[q];
            if (dfs(b, w, m, n, k + 1)) return true;
        }
		*/
        b[i][j] = temp;
        return res;
    }
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210713220624331.png)




![在这里插入图片描述](https://img-blog.csdnimg.cn/20210713221503205.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RlRnVpcm5ldmVy,size_16,color_FFFFFF,t_70#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210713221511644.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RlRnVpcm5ldmVy,size_16,color_FFFFFF,t_70#pic_center)






## 4、复杂度
```cpp
/*
时间复杂度 O(3^K MN) ： 最差情况下，需要遍历矩阵中长度为 K 字符串的所有方案，
时间复杂度为 O(3^K)；矩阵中共有 MN 个起点，时间复杂度为 O(MN) 。
空间复杂度 O(K) ： 搜索过程中的递归深度不超过 K ，因此系统因函数调用累计使用的栈空间占用 O(K)
 （因为函数返回后，系统调用的栈空间会释放）。
 最坏情况下 K=MN ，递归深度为 MN ，此时系统栈使用 O(MN) 的额外空间。
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
- 剑指 Offer（C++版本）系列：剑指 Offer 12 矩阵中的路径

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


