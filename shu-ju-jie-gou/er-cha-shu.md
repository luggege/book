### 二叉树

#### 概念

> 树：一种常用的数据结构，用来模拟具有树状结构性质的数据集合。特征：**N个节点、N-1条边**的有项无环图。  
> 二叉树：每个节点最多有**两个子树。        
> **叶子节点：没有子节点的节点。

#### 遍历方式

* 深度优先遍历
* * 前序遍历：根---左---右
  * ```js
    const node = {
        val: 1,
        left: {
            val: 2,
            left: null,
            right: null
        },
        right: {
            val: 3,
            left: {
                val: 4,
                left: null,
                right: null
            },
            right: {
                val: 5,
                left: null,
                right: null
            }
        }
    }
    ```

    ```js
    const dfs = (node) => {
        if (!node) return false
        console.log(node.val)
        dfs(node.left)
        dfs(node.right)
    }
    dfs(node) // 1 2 3 4 5
    ```
  * 中序遍历：左---根---右
  * ```js
    const dfs = (node) => {
        if (!node) return false
        dfs(node.left)
        console.log(node.val)
        dfs(node.right)
    }
    dfs(node) // 2 1 4 3 5
    ```
  * 后序遍历：左---右---根
  * ```js
    const dfs = (node) => {
        if (!node) return false
        dfs(node.left)
        dfs(node.right)
        console.log(node.val)
    }
    dfs(node) // 2 4 5 3 1
    ```
* 广度优先遍历

* * 层次遍历：根---二级邻节点（左子树、右子树）---三级邻节点
  * ```js
    let res = []
    function bfs (node, index) {
        if (!node) return
        if (!res[index]) {
            res[index] = []
        }
        res[index].push(node.val)
        bfs(node.left, index + 1)
        bfs(node.right, index + 1)
        return res
    }
    bfs (node, 0)   // [[1], [2, 3], [4, 5]]
    ```

##### 深度优先搜索（DFS）：栈的应用

> 查找根节点到目标节点的路径（找到的第一条路径不一定是最短路径）。
>
> 栈的入栈和出栈顺序：首先将根节点推入到栈中，然后将第一个邻居节点推入到栈中，当到达最深的节点而没有找到目标节点的时候，需要回溯，回溯时，弹出栈中最深的节点，即最后一个节点，在重新查找，以此类推。。。

##### 广度优先搜索（BFS）：队列的应用

> BFC是一种遍历或搜索数据结构的算法。常见应用是：找出根节点到目标节点的最短路径。
>
> 队列的入队和出队顺序：首先将根节点排入队列，然后在每一轮中，我们逐个处理已经在队列中的节点，并将所有邻居节点添加到队列中。值得注意的是，新添加的节点不会立即遍历，而是在下一轮中处理。

#### 运用递归解决问题

* 解决方案
* * “自顶向下“：前序遍历
  * “自底向上“：后序遍历
* 二叉树的最大深度：根节点到最远叶子节点的最长路径上的节点数



