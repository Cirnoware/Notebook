
## 教材

《Data Structures and Algorithms Analysis in C》  

## 成绩构成

- 作业 10%
- 小测 10%
- 期中 15%(冬学期第二周)
- 期末 40%
(皆为单独命题考试，内容以PPT为主)
- 大作业 30% (Hard，互评50%，助教50%) 

## 大作业提交

  > 交两次，第一次在PR中互评，第二次在final中交给助教 

---  
## 01 What to analyze 
Time & Space complexity(machine & complier dependent)  
- $T_{avg}(N)\enspace\& \enspace T_{worst}(N)$

### 定义
- $T(N) = O(f(N))$ : if there are positive constants c and n0 such that  $T (N) \leq c \cdot f (N)$ for all $N \geq n_0$. (即上界)
- $T(N) = \Omega(g(N))$ : if there are positive constants c and n0 such that  $T (N) \geq c \cdot g (N)$ for all $N \leq n_0$. (即下界)
- $T(N) = \Theta(h(N))$ : if there are positive constants c and n0 such that  $T (N) = c \cdot h (N)$ for all $N = n_0$. (即确定性的算法，如if)
- $T(N) = o(p(N))$ : if there are positive constants c and n0 such that  $T (N) \geq c \cdot p (N)$ for all $N \leq n_0$. (无限接近不等于)

### 运算法则
- 相加：取最大
- 相乘：相乘
- 当T(N)为k阶多项式时,$T(N) = \Theta(N^k)$
- $log_k N = O(N)$，对任意的k

### 一般规则
- for循环：T = 循环内部的代码 * 循环次数
- 嵌套for循环：循环内部的代码 * 每一层循环的次数的乘积
- 顺序执行的代码：由最大的决定
- 分支语句：T = 条件判断 + 两个分支中较大的那个
```
    if (condition) S1  
    else s2
```

- 递归：
$(\frac{3}{2})^2 \leq Fib(N) \leq (\frac{5}{2})^n$


### 分治法
> 将一个n的方法变为$\frac{n}{2}$的方法

---

## 02 列表，栈，队列
### 抽象数据类型（ADT）
> Data Type = { Objects } + { Operations }  

### List
  1. 数组实现
  2. 链表  
    dummy node：头结点，不存储数据，只是为了方便操作（即表头）

### 栈：LIFO
  - 操作：Push（进栈），Pop（出栈），Top  
  
    > 从空栈中pop，或者向满栈push，都会导致出错（仅在数组实现时产生）

  1. 栈实现
     - 减少free和malloc：设置recycle bin

  - 应用之一：括号匹配
  - 
    > 用栈实现，遇到左括号入栈，遇到右括号出栈，最后栈空则匹配成功

  - 应用之二：计算器实现
  
    > 用栈实现，将中缀表达式转换为后缀表达式->计算后缀表达式

    - 表达式转换：运算符入栈  
      读入优先级$\geq$原先优先级：入栈  
      关于括号：左括号在入栈前优先级最高，在入栈后优先级最低
  
  - 应用之三：函数调用
    
### 队列：FIFO
  - 操作：Enqueue（入队），Dequeue（出队），Front（头，出队），Rear（尾，入队）
  - 循环队列：用数组实现，头尾相接，头指针指向队头，尾指针指向队尾的下一个位置
    - 判断循环队列是否已存满：
      1. 使用size变量
      2. 使用一个空间作为标记
  
---

## 03 树
### 一、属性
  - degree of a node ::= number of subtrees of the node.  For example, degree(A) = 3, degree(F) = 0.(For a binary tree, degree of a node is either 0 or 1 or 2.)
  - degree of a tree ::= maximum degree of all nodes in the tree.  For example, degree(T) = 3.
  - parent ::= 有子树的节点
  - child ::= 有父节点的节点（母节点的子树的根）
  - sibling ::= 具有同一母节点的节点
  - leaf ::= 没有子树的节点
  - path ::= 从一个节点到另一个节点的路径（唯一）
  - length of a path ::= number of edges on the path
  - depth of a node ::= length of the path from the root to the node,Depth(root) = 0
  - height of a node ::= length of the longest path from the node to a leaf
  - ancestors of a node ::= all nodes on the path from the root to the node
  - descendants of a node ::= all nodes on the path from the node to a leaf

### 二、实现（链表）

### 三、树的遍历（四种）
  - Preorder：先访问根
  - Postorder：最后访问根
  - Level-order
  - Inorder：最先访问根  
  #### 1. 性质  
    1. 叶的顺序不变
    2. 任何数都可以转换成一个二叉树（见PPT04P06）

### 四、Threaded Bindary Trees 
  Thread == Ture:原来是一个空指针
  - 为每个节点添加一个线索，指向中序遍历的后继节点
  - 为每个节点添加一个线索，指向中序遍历的前驱节点

### 五、Properties of Binary Trees
  - For any nonempty binary tree, n0 = n2 + 1 where n0 is the number of leaf nodes and n2 the number of nodes of degree 2.
  （n0为叶节点数，n2为度为2的节点数，即有两个子树的节点）

### 六、Binary Search Tree
  > 正序：increasing order

  1. 性质  
     - 左子树的所有节点的值均小于根节点的值，右子树的所有节点的值均大于根节点的值
     - 键值全为整数且不同
  - For find operation:T(N) = O(d),d is the depth of the tree
  - Insertion
  - Delete
    1. Delete a leaf:Reset its parent link to NULL
    2. Deleta a degree 1 node :Replace the node by its single child.
    3. degree 2 node :   
        Step1: Replace the node by the largest one in its left subtree or the smallest one in its right subtree.  
        Step2: Delete the replacing node from the subtree.
  - Best case: O(logN)  全二叉树
  - Worst case: O(N)  类似链表

### 七、树的种类
  - 二叉树
  - 满二叉树
  - 完全(Complete)二叉树：除了最后一层，其他层都是满的，且最后一层的节点都靠左
    - 左子树的大于等于右子树
---

## 04 堆 (Priotiry Queues)
### 一、操作
  - 插入
  - 删除
  
### 二、二分堆(Binary Heap == Binary Queue)
#### 1.结构特性
  - 完全二叉树
  
  ```mermaid
  graph TD
  A((1))-->B((2))
  A-->C((3))
  B-->D((4))
  B-->E((5))
  C-->F((6))
  C-->G((7))
  D-->H((8))
  D-->I((9))
  ```
  - 任意节点的值大于其子节点的值
  - 任意节点的值小于其父节点的值

  - 用数组实现
    - 从1开始编号
    - 对于某个节点：（若结果符合条件，否则就说明没有）
      - 父节点编号为\[i/2\](对于某个节点)
      - 左子节点编号为2i
      - 右子节点编号为2i+1
#### 2.顺序特性
  ![](DS/4.2.2.png)
  min tree:父节点小于等于子节点，最小在树根（注意这里左节点不一定小于右节点）

#### 3.基础堆操作：基于上面的要求，完成目的           
  1. Insert（向上置换）
  2. DeleteMin（向下置换）
  3. BuildHeap
     - 从最后一个非叶节点开始，向下置换<mark>(注意不是从根节点开始一个一个插入)<mark>

---

## 05 Disjoint Sets 并查集
### 1.等价关系R
> 定义在集合上的关系
  - Reflexive 自反性：$aRa$
  - Symmetric 对称性：$aRb\ \Leftrightarrow \ bRa$
  - Transitive 传递性：$aRb \wedge bRc \Rightarrow aRc$
### 2.动态等价关系

### 3.基本操作

  > 并查的过程，就是将本身分散的节点之间建立联系的过程

  1. MakeSet(x)：建立一个新的集合，该集合中只包含元素x
  2. Set Union(x,y)：将包含元素x和y的两个集合合并成一个新的集合
     - $S_1 \cup S_2：以S_1的根为根$（谁在后边，改的就是谁的根）
  3. Find(x)：找到包含元素x的集合的名字

### 4.实现
  1. 数组实现：S[Elements]= The element's parent
     - S[0]不使用
     > 在这里，我们假定S是一个数组，数组的下标是元素的名字，数组的值是元素的父节点的名字。对于根节点的元素，可以有多种表示方法，比如0，-size等等。注意S表示的是所有元素（森林），其中可以有很多棵树（集合）

     > S[Root] = 0 （可能有好多个Root）

     ```
     SetType  Find ( ElementType X, DisjSet S ){
         for ( ; S[X] > 0; X = S[X] ) ;
     return  X ;
     }
     ```

  2. 链表实现

### 5.Smart Union Algorithms
  - Union by Size
  
    > S[Root] = -Size

    此时有$Height < \lfloor log(N) \rfloor+1$

  - Union by Height

  这些手段都是针对“并”这个过程来说的。举个例子，以按大小合并为例，当我们要合并两个集合时，我们可以先判断两个集合的大小，然后将小的集合合并到大的集合中，这样就可以保证树的高度不会太高，从而提高Find的效率。


### 6.路径压缩
  > 在Find的过程中，将路径上的所有节点也顺便都连接到根节点上
  - 和Size Union一起使用
  - 和Height Union一起使用：Union by Rank(Estimated Height)
  最差情形：![](./DS/5.6.1.png)  

---以上为期中考试内容---
