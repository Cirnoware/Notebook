
## 教材

《Data Structures and Algorithms Analysis in C》  

## 成绩构成

- 作业 10%
- 小测 10%
- 期中 15%(冬学期第二周)
- 期末 40%
(皆为单独命题考试，内容以PPT为主)
- 大作业 30% (Hard，互评50%，助教50%)  
  
## What to analyze 
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