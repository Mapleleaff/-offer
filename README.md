# 《剑指offer》第二版 Python 实现及解题思路
[题3.1-找出数组中重复的数字](题3.1-找出数组中重复的数字.py)   
**要求时间复杂度 O(N)，空间复杂度 O(1)** 。因此不能使用排序的方法，也不能使用额外的标记数组。对于这种数组元素在 [0, n-1] 范围内的问题，可以将值为 i 的元素调整到第 i 个位置上进行求解。以 (2, 3, 1, 0, 2, 5) 为例，遍历到位置 4 时，该位置上的数为 2，但是第 2 个位置上已经有一个 2 的值了，因此可以知道 2 重复

[题3.2-不修改数组找出重复的数字](题3.2-不修改数组找出重复的数字.py)     
**时间复杂度 O(NlogN)，空间复杂度 O(1)** 。二分查找方法。以长度为 8 的数组 {2, 3, 5, 4, 3, 2, 6, 7} 为例，那么所有数字都在 1-7 的范围内。中间的数字 4 将 1-7 分为 1-4 和 5-7。统计 1-4 内数字的出现次数，它们一共出现了 5 次，说明 1-4 内必要重复的数字；反之，若小于等于 4 次，则说明 5-7 内必有重复的数字。因为不能使用额外的空间，所以每次统计次数都要重新遍历整个数组一次

[题4-二维数组中的查找](题4-二维数组中的查找.py)      
**时间复杂度 O(M+N)** 。从数组右上角或者左下角开始查找 array[i][j]

[题5-替换空格](题5-替换空格.py)    
**时间复杂度 O(N)** 。如果直接每次遇到空格添加 "%20"，那么空格后面的数字就需要频繁向后移动。遇到这种移动问题，可以尝试先遍历一次，找出空格的数量，得到替换后的长度，然后从后往前扫描替换。逆向思维

[题6-从尾到头打印链表](题6-从尾到头打印链表.py)       
（1）从头到尾遍历链表，并用栈存储每个结点的值，之后出栈输出
（2）使用递归方法

[题7-重构二叉树](题7-重构二叉树.py)     
利用二叉树前序遍历和中序遍历的特性。前序遍历的第一个值为根节点的值，使用这个值将中序遍历结果分成两部分，左部分为树的左子树中序遍历结果，右部分为树的右子树中序遍历的结果。然后递归

[题8-二叉树的下一个结点](题8-二叉树的下一个结点.py)     
若该节点存在右子树：则下个节点为右子树最左子节点；
若该节点不存在右子树：这时分两种情况：该节点为父节点的左子节点，则下一个节点为其父节点。该节点为父节点的右子节点，则沿着父节点向上遍历，直到找到一个节点，该结点是其父节点的左子节点，则该节点的父节点就是下一个节点

[题9-用两个栈实现队列](题9-用两个栈实现队列.py)     
假设 stack_in 用于处理入栈操作，stack_out 用于处理出栈操作，stack_in 按栈的方式正常处理入栈数据。关键在于出栈操作。当 stack_out 为空时，需要先将每个 stack_in 中的数据出栈后压入 stack_out。反之，每次弹出 stack_out 栈顶元素即可

[题10.1-斐波那契数列](题10.1-斐波那契数列.py)    
三种思路（1）递归（2）循环，**时间复杂度O(N)** （3）求矩阵的乘方，**时间复杂度O(logN)**

[题10.2-青蛙跳台阶问题](题10.2-青蛙跳台阶问题.py)    
斐波那契数列问题

[题11-旋转数组的最小数字](题11-旋转数组的最小数字.py)   
假设第一个指针总是指向前面递增数组的元素，第二个指针总是指向后面递增数组的元素。最终它们会指向两个相邻的元素，而第二个指针指向的刚好是最小的元素，这就是循环结束的条件；如果把排序数组的 0 个元素搬到最后面，这仍然是旋转数组，我们的代码需要支持这种情况。如果发现数组中的一个数字小于最后一个数字，就可以直接返回第一个数字了；下面这种情况，即第一个指针指向的数字、第二个指针指向的数字和中间的数字三者相等，我们无法判断中间的数字 1 是数以前面的递增子数组还是后面的递增子数组。这样的话，我们只能进行顺序查找

[题12-矩阵中的路径](题12-矩阵中的路径.py)   
使用回溯法（backtracking）进行求解。它是一种暴力搜索方法，通过搜索所有可能的结果来求解问题。回溯法在一次搜索结束时需要进行回溯（回退），将这一次搜索过程中设置的状态进行清除，从而开始一次新的搜索过程。步骤 1，将 matrix 字符串模拟映射为一个字符矩阵（但并不实际创建一个矩阵）。步骤 2，取一个 boolean[matrix.length] 标记某个字符是否已经被访问过。如果没找到结果，需要将对应的 boolean 标记值置回 false，返回上一层进行其他分路的查找

[题13-机器人的运动范围](题13-机器人的运动范围.py)  
同题 12 的思路一样，判断条件改成行坐标和列坐标的数位之和大于 k

[题14-剪绳子](题14-剪绳子.py)
（1）动态规划。**时间复杂度：O(N^2)，空间复杂度：O(N)**    
递推公式    
f(n) = 0，n = 1   
f(n) = 1，n = 2    
f(n) = 2，n = 3      
f(n) = max{ dp(i) * dp(n-i) } n > 3, 1<= i <=n-1   

注意：    
当 n <= 3 时因为必须剪至少一次的缘故，导致 f(1)=0, f(2)=1*1=1, f(3)=1*2=2；
当 n >=4 时，将 n<=3 的部分单独作为一段能提供更大的乘积
因此，初始化时应该 dp[1]=1≠f(1), dp[2]=2≠f(2), dp[3]=3≠f(3)，同时将 f(1), f(2), f(3) 单独返回

[题21-调整数组顺序使奇数位于偶数前面](题21-调整数组顺序使奇数位于偶数前面.py)     
（1）使用新列表，奇数存一个列表，偶数存一个列表，合并
（2）使用冒泡的思想
（3）注重函数的扩展性能。把函数中的判断条件写成一个判断条件的函数，方便与函数的扩展。对于奇数位于偶数前面的情况，类似于快排，在头和尾分别设置一个指针，头指针指向奇数则后移，尾指针指向偶数则前移。

[题22-链表中倒数第K个节点](题22-链表中倒数第K个节点.py)     
如果输入链表为空，K 小于等于 0，K 大于链表的长度，返回 None；如果正常情况，设置两个指针 p1, p2 分别指向头节点，p1 指针先向前走 K-1 步，走到正数第 K 个节点，然后两指针分别往前移动，直到 p1 走到最后一个节点

[题23-链表中环的入口节点](题23-链表中环的入口节点.py)     
使用双指针，一个指针 fast 每次移动两个节点，一个指针 slow 每次移动一个节点。因为存在环，所以两个指针必定相遇在环中的某个节点上。假设相遇点在下图的 z1 位置（图片这里没放），此时 fast 移动的节点数为 x+2y+z，slow 为 x+y，由于 fast 速度比 slow 快一倍，因此 x+2y+z=2(x+y)，得到 x=z。在相遇点，slow 要到环的入口点还需要移动 z 个节点，如果让 fast 重新从头开始移动，并且速度变为每次移动一个节点，那么它到环入口点还需要移动 x 个节点。在上面已经推导出 x=z，因此 fast 和 slow 将在环入口点相遇

[题24-反转链表](题24-反转链表.py)     
（1）循环解法（2）递归解法。需要注意的问题：如果输入的链表头指针为 None；或者整个链表只有一个节点时；反转后的链表出现断裂；返回的反转之后的头节点不是原始链表的尾节点。因此需要引入 pre, cur, next 代表对应位置的节点

[题25-合并两个排序的链表](题25-合并两个排序的链表.py)  
（1）循环解法（2）递归解法。需要注意代码鲁棒性问题，防止如空链表输入造成崩溃等

[题26-树的子结构](题26-树的子结构.py)
递归判断树的每个节点是否相同。需要注意输入的结点为空或者输入的结点没有子树的情况。
其中判断 pRoot 是否为 None 的两个 if 语句不可以颠倒顺序，如果颠倒顺序，会先判断 pRoot1 是否为 None，其实这个时候 pRoot2 的结点已经遍历完成确定相等了，但是返回了 False，判断错误
