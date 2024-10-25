## 思维导航

* [前言](https://github.com)
* [C\#二分查找算法](https://github.com)
* [C\#线性查找算法](https://github.com)
* [C\#二叉搜索树算法](https://github.com)
* [C\#哈希查找算法](https://github.com)

## 前言


在编程领域，数据结构与算法是构建高效、可靠和可扩展软件系统的基石。它们对于提升程序性能、优化资源利用以及解决复杂问题具有至关重要的作用。今天大姚给大家分享四种C\#中常见的经典查找算法。


* **C\#数据结构与算法实战入门指南：** [https://mp.weixin.qq.com/s/XPRmwWmoZa4zq29Kx\-u4HA](https://github.com)
* **欢迎加入DotNetGuide技术社区交流群：** [https://mp.weixin.qq.com/s/07UYvW8uuspWaaBrWjw2MQ](https://github.com):[楚门加速器](https://shexiangshi.org)


## C\#二分查找算法


### 简介


二分查找算法是一种在有序数组中查找特定元素的搜索算法。


* **详细文章描述：** [https://mp.weixin.qq.com/s/uCuqv0zOI0ZsF48Q1LoCsQ](https://github.com)


### 代码实现



```
public class 二分查找算法
    {
        /// 
        /// 二分查找算法
        /// 
        /// arr是已排序的数组
        /// target是要查找的目标值
        /// 目标值在数组中的索引，如果未找到则返回-1
        public static int BinarySearch(int[] arr, int target)
        {
            int left = 0; // 定义左指针
            int right = arr.Length - 1; // 定义右指针

            while (left <= right)
            {
                // 计算中间元素的索引
                int mid = left + (right - left) / 2;

                if (arr[mid] == target)
                {
                    // 如果中间元素等于目标值
                    return mid; // 查找成功，返回索引
                }
                else if (arr[mid] < target)
                {
                    // 如果目标值小于中间元素，则在左半部分查找
                    left = mid + 1;
                }
                else
                {
                    // 如果目标值大于中间元素，则在右半部分查找
                    right = mid - 1;
                }
            }

            // 未找到 target，返回-1
            return -1;
        }

        public static void BinarySearchRun()
        {
            int[] arr = { 1, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59 }; //注意：这里的数组是已排序的数组
            int target = 31; //需要要查找的目标值

            int result = BinarySearch(arr, target); //调用二分查找方法

            if (result == -1)
            {
                Console.WriteLine("元素未找到");
            }
            else
            {
                Console.WriteLine($"元素找到，索引为：{result}，值为：{arr[result]}");
            }
        }
    }

```

## C\#线性查找算法


### 简介


线性查找算法是一种简单的查找算法，用于在一个数组或列表中查找一个特定的元素。它从数组的第一个元素开始，逐个检查每个元素，直到找到所需的元素或搜索完整个数组。线性查找的时间复杂度为O(n)，其中n是数组中的元素数量。


* **详细文章描述：** [https://mp.weixin.qq.com/s/VKC5lEYCL7SHieNMaPOE3A](https://github.com)


### 代码实现



```
  public static void LinearSearchRun()
        {
            int[] arr = { 2, 3, 4, 10, 40, 50, 100, 77, 88, 99 };
            int target = 100;

            int result = LinearSearch(arr, target);

            // 输出结果
            if (result == -1)
            {
                Console.WriteLine("元素未找到");
            }
            else
            {
                Console.WriteLine($"元素在索引 {result} 处找到，index = {result}");
            }
        }

        /// 
        /// 线性查找函数
        /// 
        /// arr
        /// target
        /// 
        public static int LinearSearch(int[] arr, int target)
        {
            // 遍历数组
            for (int i = 0; i < arr.Length; i++)
            {
                // 如果找到目标值，返回其索引
                if (arr[i] == target)
                {
                    return i;
                }
            }
            // 如果没有找到，则返回-1
            return -1;
        }

```

## C\#二叉搜索树算法


### 简介


二叉搜索树（Binary Search Tree，简称BST）是一种节点有序排列的二叉树数据结构。


* **详细文章描述：** [https://mp.weixin.qq.com/s/qs8CZzjtmyXkQhkRWmqllA](https://github.com)


### 代码实现



```
namespace HelloDotNetGuide.常见算法
{
    public class 二叉搜索树算法
    {
        public static void BinarySearchTreeRun()
        {
            var bst = new BinarySearchTree();

            // 插入一些值到树中
            bst.Insert(50);
            bst.Insert(30);
            bst.Insert(20);
            bst.Insert(40);
            bst.Insert(70);
            bst.Insert(60);
            bst.Insert(80);
            bst.Insert(750);

            Console.WriteLine("中序遍历（打印有序数组）：");
            bst.InorderTraversal();

            Console.WriteLine("\n");

            // 查找某些值
            Console.WriteLine("Search for 40: " + bst.Search(40)); // 输出: True
            Console.WriteLine("Search for 25: " + bst.Search(25)); // 输出: False

            Console.WriteLine("\n");

            // 删除某个值
            bst.Delete(50);
            Console.WriteLine("删除50后：");
            bst.InorderTraversal();
        }
    }

    /// 
    /// 定义二叉搜索树的节点结构
    /// 
    public class TreeNode
    {
        public int Value;
        public TreeNode Left;
        public TreeNode Right;

        public TreeNode(int value)
        {
            Value = value;
            Left = null;
            Right = null;
        }
    }

    /// 
    /// 定义二叉搜索树类
    /// 
    public class BinarySearchTree
    {
        private TreeNode root;

        public BinarySearchTree()
        {
            root = null;
        }

        #region 插入节点

        /// 
        /// 插入新值到二叉搜索树中
        /// 
        /// value
        public void Insert(int value)
        {
            if (root == null)
            {
                root = new TreeNode(value);
            }
            else
            {
                InsertRec(root, value);
            }
        }

        private void InsertRec(TreeNode node, int value)
        {
            if (value < node.Value)
            {
                if (node.Left == null)
                {
                    node.Left = new TreeNode(value);
                }
                else
                {
                    InsertRec(node.Left, value);
                }
            }
            else if (value > node.Value)
            {
                if (node.Right == null)
                {
                    node.Right = new TreeNode(value);
                }
                else
                {
                    InsertRec(node.Right, value);
                }
            }
            else
            {
                //值已经存在于树中，不再插入
                return;
            }
        }

        #endregion

        #region 查找节点

        /// 
        /// 查找某个值是否存在于二叉搜索树中
        /// 
        /// value
        /// 
        public bool Search(int value)
        {
            return SearchRec(root, value);
        }

        private bool SearchRec(TreeNode node, int value)
        {
            // 如果当前节点为空，表示未找到目标值
            if (node == null)
            {
                return false;
            }

            // 如果找到目标值，返回true
            if (node.Value == value)
            {
                return true;
            }

            // 递归查找左子树或右子树
            if (value < node.Value)
            {
                return SearchRec(node.Left, value);
            }
            else
            {
                return SearchRec(node.Right, value);
            }
        }

        #endregion

        #region 中序遍历

        /// 
        /// 中序遍历（打印有序数组）
        /// 
        public void InorderTraversal()
        {
            InorderTraversalRec(root);
        }

        private void InorderTraversalRec(TreeNode root)
        {
            if (root != null)
            {
                InorderTraversalRec(root.Left);
                Console.WriteLine(root.Value);
                InorderTraversalRec(root.Right);
            }
        }

        #endregion

        #region 删除节点

        /// 
        /// 删除某个值
        /// 
        /// val
        public void Delete(int val)
        {
            root = DeleteNode(root, val);
        }

        private TreeNode DeleteNode(TreeNode node, int val)
        {
            if (node == null)
            {
                return null;
            }

            if (val < node.Value)
            {
                node.Left = DeleteNode(node.Left, val);
            }
            else if (val > node.Value)
            {
                node.Right = DeleteNode(node.Right, val);
            }
            else
            {
                // 节点有两个子节点
                if (node.Left != null && node.Right != null)
                {
                    // 使用右子树中的最小节点替换当前节点
                    TreeNode minNode = FindMin(node.Right);
                    node.Value = minNode.Value;
                    node.Right = DeleteNode(node.Right, minNode.Value);
                }
                // 节点有一个子节点或没有子节点
                else
                {
                    TreeNode? temp = node.Left != null ? node.Left : node.Right;
                    node = temp;
                }
            }

            return node;
        }

        /// 
        /// 找到树中的最小节点
        /// 
        /// 
        /// 
        private TreeNode FindMin(TreeNode node)
        {
            while (node.Left != null)
            {
                node = node.Left;
            }
            return node;
        }

        #endregion
    }
}

```

## C\#哈希查找算法


### 简介


哈希查找算法是一种高效的查找算法，通过将键值映射到哈希表中的位置来实现快速访问。在C\#中，哈希查找通常通过哈希表（Hashtable）或字典（Dictionary）来实现。


* **详细文章描述：** [https://mp.weixin.qq.com/s/WaXCFshzuqVQD6YX2Kcw5g](https://github.com)


### 代码实现



```
 public class 哈希查找算法
    {
        /// 
        /// 哈希查找函数
        /// 
        /// target
        public static void HashSearchFunctionRun(int target)
        {
            //创建一个字典来存储键值对
            var dic = new Dictionary<int, string>();
            dic.Add(1, "one");
            dic.Add(2, "two");
            dic.Add(3, "three");

            //查找目标值是否在Dictionary中存在
            //TryGetValue方法可以返回一个bool值和值，如果找到了目标值，则返回true和对应的值，否则返回false和默认值
            string value;
            if (dic.TryGetValue(target, out value))
            {
                Console.WriteLine("Found Data: " + value);
            }
            else
            {
                Console.WriteLine("Not Found Data.");
            }
        }
    }

```

 
