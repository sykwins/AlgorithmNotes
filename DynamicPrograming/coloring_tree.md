#### 题目描述
对一棵树进行着色，每个结点可着黑色或白色，相邻结点不能着相同黑色，但可着相同白色  
令树的根为r，请设计一种算法对树中尽量多的节点着黑色

#### 解题思路
用`0`代表白色`1`代表黑色    
根节点`r`可以着白色或黑色  
用`T[r][0]`和`T[r][1]`表示根节点着白色和黑色的结果  
问题的最优解：`c = max{T[r][0], T[r][1]}`  
设`r`有`m`个子节点，记为`Si`，`1 <= i <= m`，则  
`T[r][0] = sum(i=1~m){max(T[Si][0],T[Si][0])}`  
`T[r][1] = sum(i=1~m){T[Si][0]} + 1`