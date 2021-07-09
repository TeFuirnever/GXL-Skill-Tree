@[toc]

## 同步GitHub在此 👉 [https://github.com/TeFuirnever/GXL-Skill-Tree](https://github.com/TeFuirnever/GXL-Skill-Tree)

- [剑指 Offer（C++版本）系列：总目录和一些提高效率的说明](https://tefuirnever.blog.csdn.net/article/details/118423883)
- [剑指 Offer（C++版本）系列：剑指 Offer 03 数组中重复的数字](https://tefuirnever.blog.csdn.net/article/details/118445391)
- [剑指 Offer（C++版本）系列：剑指 Offer 04 二维数组中的查找](https://tefuirnever.blog.csdn.net/article/details/118467105)
- [剑指 Offer（C++版本）系列：剑指 Offer 05 替换空格](https://tefuirnever.blog.csdn.net/article/details/118498159)
- [剑指 Offer（C++版本）系列：剑指 Offer 06 从尾到头打印链表](https://tefuirnever.blog.csdn.net/article/details/118529012)
- [剑指 Offer（C++版本）系列：剑指 Offer 07 重建二叉树](https://tefuirnever.blog.csdn.net/article/details/118557615)

## 1、题干
```

重建二叉树

输入某二叉树的前序遍历和中序遍历的结果，请重建该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。


例如，给出

前序遍历 preorder = [3,9,20,15,7]
中序遍历 inorder = [9,3,15,20,7]
返回如下的二叉树：

    3
   / \
  9  20
    /  \
   15   7
 

限制：

0 <= 节点个数 <= 5000

通过次数158,941提交次数228,915


```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210707211850105.png)


## 2、递归法
首先复习一下三种遍历：
- 前序遍历：根节点 | 左子树 | 右子树；
- 中序遍历：左子树 | 根节点 | 右子树；
- 后序遍历：左子树 | 根节点 | 右子树；

然后，重建二叉树，需要知道根节点，左节点，右节点，那么就能重建，这就需要中序遍历，确定根节点所在位置，继而确定左右边界。

最后，当 left > right ，代表已经越过叶节点，此时返回 nullptr ；

算法流程：
1. 首先初始化一个哈希表，保存中序遍历值对应的索引；
2. 递归重建二叉树；
	1. 判断递归终止条件：无论是左子树还是右子树，left > right 都终止；
	2. 前序遍历的最左面结点是根节点的值 rootval ，根节点在中序遍历对应的即为根节点到左边界的长度 k；
	3. 建立根节点 root ： new TreeNode(rootval);
	4. 构建左右子树： 开启左右子树递归；

|	|前序遍历左边界	|前序遍历右边界|中序遍历左边界	|中序遍历右边界|
|--|--|--|--|--|
|左子树	|pl + 1|pl + 1 + len| il| k - 1|
|右子树	|pl + 1 + len| pr| k + 1| ir|

3. 返回值： 根节点 root ，作为上一层递归中根节点的左 / 右子节点；

```cpp
//面试题07.重建二叉树
//标准做法
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
	unordered_map<int, int> pos;
	TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
		int n = preorder.size();
		for (int i = 0; i<n; ++i) pos[inorder[i]] = i;
		return dfs(preorder, inorder, 0, n - 1, 0, n - 1);
	}
	
	TreeNode* dfs(vector<int>& preorder, vector<int>& inorder, int pl, int pr, int il, int ir)
	{
		if (pl>pr) return nullptr;
		if (il>ir) return nullptr;
		int rootval = preorder[pl];
		int k = pos[rootval];
		int len = k - il;
		auto root = new TreeNode(rootval);
		root->left = dfs(preorder, inorder, pl + 1, pl + 1 + len, il, k - 1);
		root->right = dfs(preorder, inorder, pl + 1 + len, pr, k + 1, ir);
		return root;
	}
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210707220701401.png)



![在这里插入图片描述](https://img-blog.csdnimg.cn/2021070722251153.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210707222518933.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210707222525629.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/2021070722253299.png)


## 4、复杂度
```cpp
/*
时间复杂度：O(n)。对于每个节点都有创建过程以及根据左右子树重建过程。
空间复杂度：O(n)。存储整棵树的开销。
*/
```

——————————————————————————————————————

- [剑指 Offer（C++版本）系列：总目录和一些提高效率的说明](https://tefuirnever.blog.csdn.net/article/details/118423883)
- [剑指 Offer（C++版本）系列：剑指 Offer 03 数组中重复的数字](https://tefuirnever.blog.csdn.net/article/details/118445391)
- [剑指 Offer（C++版本）系列：剑指 Offer 04 二维数组中的查找](https://tefuirnever.blog.csdn.net/article/details/118467105)
- [剑指 Offer（C++版本）系列：剑指 Offer 05 替换空格](https://tefuirnever.blog.csdn.net/article/details/118498159)
- [剑指 Offer（C++版本）系列：剑指 Offer 06 从尾到头打印链表](https://tefuirnever.blog.csdn.net/article/details/118529012)
- [剑指 Offer（C++版本）系列：剑指 Offer 07 重建二叉树](https://tefuirnever.blog.csdn.net/article/details/118557615)

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


