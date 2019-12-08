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
（1）从头到尾遍历链表，并用栈存储每个结点的值，之后出栈输出。
（2）使用递归方法

[题7-重构二叉树](题7-重构二叉树.py)     
利用二叉树前序遍历和中序遍历的特性。前序遍历的第一个值为根节点的值，使用这个值将中序遍历结果分成两部分，左部分为树的左子树中序遍历结果，右部分为树的右子树中序遍历的结果。然后递归

[题8-二叉树的下一个结点](题8-二叉树的下一个结点.py)     
若该节点存在右子树：则下个节点为右子树最左子节点；
若该节点不存在右子树：这时分两种情况：该节点为父节点的左子节点，则下一个节点为其父节点。该节点为父节点的右子节点，则沿着父节点向上遍历，直到找到一个节点，该结点是其父节点的左子节点，则该节点的父节点就是下一个节点

[题9-用两个栈实现队列](题9-用两个栈实现队列.py)     
假设 stack_in 用于处理入栈操作，stack_out 用于处理出栈操作，stack_in 按栈的方式正常处理入栈数据。关键在于出栈操作。当 stack_out 为空时，需要先将每个 stack_in 中的数据出栈后压入 stack_out。反之，每次弹出 stack_out 栈顶元素即可

[题10.1-斐波那契数列](题10.1-斐波那契数列.py)    
三种思路（1）递归（2）循环，**时间复杂度 O(N)** （3）求矩阵的乘方，**时间复杂度 O(logN)**

[题10.2-青蛙跳台阶问题](题10.2-青蛙跳台阶问题.py)    
斐波那契数列问题

[题11-旋转数组的最小数字](题11-旋转数组的最小数字.py)   
假设第一个指针总是指向前面递增数组的元素，第二个指针总是指向后面递增数组的元素。最终它们会指向两个相邻的元素，而第二个指针指向的刚好是最小的元素，这就是循环结束的条件；如果把排序数组的 0 个元素搬到最后面，这仍然是旋转数组，我们的代码需要支持这种情况。如果发现数组中的一个数字小于最后一个数字，就可以直接返回第一个数字了；下面这种情况，即第一个指针指向的数字、第二个指针指向的数字和中间的数字三者相等，我们无法判断中间的数字 1 是数以前面的递增子数组还是后面的递增子数组。这样的话，我们只能进行顺序查找

[题12-矩阵中的路径](题12-矩阵中的路径.py)   
使用回溯法（backtracking）进行求解。它是一种暴力搜索方法，通过搜索所有可能的结果来求解问题。回溯法在一次搜索结束时需要进行回溯（回退），将这一次搜索过程中设置的状态进行清除，从而开始一次新的搜索过程。步骤 1，将 matrix 字符串模拟映射为一个字符矩阵（但并不实际创建一个矩阵）。步骤 2，取一个 boolean[matrix.length] 标记某个字符是否已经被访问过。如果没找到结果，需要将对应的 boolean 标记值置回 false，返回上一层进行其他分路的查找

[题13-机器人的运动范围](题13-机器人的运动范围.py)  
同题 12 的思路一样，判断条件改成行坐标和列坐标的数位之和大于 k

[题14-剪绳子](题14-剪绳子.py)   
（1）动态规划。**时间复杂度 O(N^2)，空间复杂度 O(N)**    
递推公式：f(n) = 0，n = 1；f(n) = 1，n = 2；f(n) = 2，n = 3；f(n) = max{ dp(i) x dp(n-i) }，n > 3, 1<= i <=n-1   
注意：当 n <= 3 时因为必须剪至少一次的缘故，导致f(1) = 0；f(2) = 1x1=1；f(3) = 1x2=2。当 n>=4 时，将 n<=3 的部分单独作为一段能提供更大的乘积   因此，初始化时应该 dp[1]=1≠f(1), dp[2]=2≠f(2), dp[3]=3≠f(3)，同时将 f(1), f(2), f(3) 单独返回        
（2）贪心算法。**时间复杂度 O(1)，空间复杂度 O(1)**     
当 n>=5 时，尽可能多剪长度为 3 的绳子。当 n=4 时，剪成两段长度为 2 的绳子     
证明：当 n >= 5 时，可以得：3(n-3) > 2(n-2) > n。当 n == 4 时，2x2 > 3x1

[题15-二进制中1的个数](题15-二进制中1的个数.py)    
（1）注意到每个非零整数 n 和 n-1 进行按位与运算，整数 n 的二进制数中最右边的1就会变成 0，那么二进制数中的 1 的个数就会减少一个，因此可以利用一个循环。使得 n = n&(n-1) ，计算经过几次运算减少到 0，就是有几个 1。（2）原始 n 左移一位和右移一位的方法，因为Python不会出现整数溢出的情况。（3）1 左移解法，循环次数为整数二进制的位数=32。（4）扩展：判断一个数值是不是 2 得整数次方，如果是的话，这个数的二进制数中有且只有一个 1，那么这个数 n 会有 n&(n-1) == 0。或者求两个整数 m 和 n 需要改变 m 二进制中的多少位才能得到 n，可以先做 m^n 的异或运算，然后求这个数中有多少个1

[题16-数值的整数次方](题16-数值的整数次方.py)  
需要注意：当指数为负数的时候；当底数为零得时候；指数为负数的情况；在判断底数 base 是不是等于 0 的时候，不能直接写 base==0，因为计算机内表示小数时有误差，只能判断他们的差的绝对值是不是在一个很小的范围内。**优化代码速度**。当 n 为偶数, a^n = a^(n/2) * a^(n/2)；当 n 为奇数, a^n = a^((n-1)/2) * a^((n-1)/2)) * a，利用右移一位运算代替除以 2，利用位与运算代替了求余运算法 % 来判断一个数是奇数还是偶数

[题17-打印从1到最大的n位数](题17-打印从1到最大的n位数.py)     
（1）在字符串表达的数字上模拟加法，把字符串表达的数字打印出来。（2）把问题转换成数字排列的解法，递归让代码更简洁

[题18.1-在O(1)时间内删除链表节点](题18.1-在O(1)时间内删除链表节点.py)   
（1）从头遍历，得到被删除节点的前一个节点，然后前一个节点指向被删除节点的下个节点
（2）把下一个节点的内容复制到需要删除的节点。对于 n-1 个非尾节点而言，我们可以在 **时间复杂度 O(1)** 内把下一个节点的内存复制，并覆盖要删除的节点，并删除下一个节点；对于尾节点，由于仍然要顺序查找，**时间复杂度是 O(n)** 。因此总的 **平均时间复杂度为 [(n-1)xO(1)+O(n)]/n**，结果还是 **O(1)** 。

[题18.2-删除链表中重复的节点](题18.2-删除链表中重复的节点.py)  
（1）将链表里面所有的数存在一个列表里面，然后把列表里面只出现一次的数提取出来，在新建一个链表放进去
（2） 设置 pre, cur 代表对应节点，顺序遍历。注意重复的节点不保留，所以要特别注意头结点也重复的情况。最好的做法是新设一个头结点

[题19-正则表达式匹配](题19-正则表达式匹配.py)   
关键在于缕清思路，考虑到所有可能性。具体情况分析看一下代码中的注释

[题20-表示数值的字符串](题20-表示数值的字符串.py)    
（1）float 强制转换。（2）正则表达式。表示数值的字符串遵循模式 A[.[B]][e|EC] 或者 .B[e|EC]，其中 A 为数值的整数部分，B 紧跟着小数点为数值的小数部分，C 紧跟着 "e" 或者 "E" 为数值的指数部分。上述 A 和 C 都是可能以 "+" 或者 "-" 开头的 0-9 的数位串，B 也是 0-9 的数位串，但前面不能有正负号

[题21-调整数组顺序使奇数位于偶数前面](题21-调整数组顺序使奇数位于偶数前面.py)     
（1）使用新列表，奇数存一个列表，偶数存一个列表，合并
（2）使用冒泡的思想
（3）注重函数的扩展性能。把函数中的判断条件写成一个判断条件的函数，方便与函数的扩展。对于奇数位于偶数前面的情况，类似于快排，在头和尾分别设置一个指针，头指针指向奇数则后移，尾指针指向偶数则前移

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

[题27-二叉树的镜像](题27-二叉树的镜像.py)  
（1）递归实现。（2）队列实现。（3）栈实现

[题28-对称的二叉树](题28-对称的二叉树.py)    
通过比较二叉树的前序遍历序列和对称前序遍历序列来判断二叉树是不是对称的，如果两个序列是一样的，那么二叉树就是对称的

[题29-顺时针打印矩阵](题29-顺时针打印矩阵.py)    
（1）魔方逆时针旋转思想。（2）暴力常规方法。首先需要判断每一步开始的坐标点是否满足小于行数的一半且小于列数的一半。然后在最后一圈中，共会出现以下四种情况，仅能向右走一行，仅能向右走一行向下走一列，向右走一行向下走一列向左走一行，能走完一整圈。其中只有能向右走一行必然发生，不必判断，剩余的都需要判断发生条件

[题30-包含min函数的栈](题30-包含min函数的栈.py)    
引入两个栈，一个栈每次 push 实际的数字，另一个 minStack。如果 push 的数字小于 minStack 栈顶的数字，minStack 中 push 新的数字，否则，把 minStack   栈顶的数字再压入一遍

[题31-栈的压入、弹出序列](题31-栈的压入、弹出序列.py)    
类似题30，借助辅助栈。建立一个辅助栈，把 push 序列的数字依次压入辅助栈，每次压入后，比较辅助栈的栈顶元素和 pop 序列的首元素是否相等，相等的话就推出   pop 序列的首元素和辅助栈的栈顶元素。若最后辅助栈为空，则 push 序列可以对应于 pop 序列

[题32.1-不分行从上到下打印二叉树](题32.1-不分行从上到下打印二叉树.py)   
队列 + 层次遍历 + 广度优先搜索

[题32.2-分行从上到下打印二叉树](题32.2-分行从上到下打印二叉树.py)    
类似题 27，题 32.1。队列 + 层次遍历 + 广度优先搜索

[题32.3-之字形打印二叉树](题32.3-之字形打印二叉树.py)    
（1）类似题 27，题 32.1，题 32.2 方法。队列 + 层次遍历 + 广度优先搜索（2）引入两个栈。在打印某一行节点时，把下一层的子节点保存到相应的栈里。如果当前打印的奇数层，则先保存左子节点再保存右子节点到第一个栈里；如果当前打印的是偶数层，则先保存右子节点再保存左子节点到第二个栈里

[题33-二叉搜索树的后序遍历序列](题33-二叉搜索树的后序遍历序列.py)   
后序遍历序列的最后一个元素为二叉树的根节点。将数组分为两部分，从左遍历找到第一个比根节点大的位置划分左右部分。左边部分所有的结点均小于根结点，右边部分所有的结点均大于根结点。然后递归查询。

[题34-二叉树中和为某一值的路径](题34-二叉树中和为某一值的路径.py)    
回溯法。类似题 12，题 13。深度优先搜索思想 DFS

[题35-复杂链表的复制](题35-复杂链表的复制.py)    
步骤 1：复制每个节点；步骤 2：遍历链表，使 A'->random = A->random->next；步骤 3：拆分链表。注意链表结点进行复制的时候，不能简单地写作 pCloned = pNode，这样的话之后对 pCloned 的操作也会作用在 pNode 上面，导致操作循环往复。需要重新定一个 pCloned = ListNode(0)，然后对结点的 .val .next .random 进行设置。同时，在将复制的结点的 random 指向原始链表结点的 random 的 next 的时候，需要先判断一下，原始链表结点的 next 是否为 None，不为None 再指向

[题36-二叉搜索树与双向链表](题36-二叉搜索树与双向链表.py)    
结合中序遍历。按照左右子树分治，递归实现。根的左边连接左子树的最右边结点，右边连接右子树的最左边结点

[题37-序列化二叉树](题37-序列化二叉树.py)    
最终要实现的是二叉树的序列化和反序列化。首先来看二叉树的序列化，二叉树的序列化就是采用前序遍历二叉树输出节点，再碰到左子节点或者右子节点为 None 的时候输出一个特殊字符 "#"。对于反序列化，就是针对输入的一个序列构建一棵二叉树，将指向位置的数字转化为二叉树的结点，左右递归实现。当遇到当前指向的字符为特殊字符 "#" 或者指针超出了序列的长度，则返回 None

[题38.1-字符串的排列](题38.1-字符串的排列.py)    
把字符串分为两部分：第一部分是字符串的第一个字符，第二部分是第一个字符以后的所有字符。第二部分字符做全排列，若还有第三部分，则递归

[题38.2-字符串的组合](题38.2-字符串的组合.py)    
类似题 38.1。思想类似

[题39-数组中出现次数超过一半的数字](题39-数组中出现次数超过一半的数字.py)    
思路为根据数组的特点，出现次数超过一半的数，他出现的次数比其他数字出现的总和还要多，因此可以最开始保存两个数值：数组中的一个数字以及它出现的次数，然后遍历，如果下一个数字等于这个数字，那么次数加 1，如果不等，次数减 1，当次数等于 0 的时候，在下一个数字的时候重新复制新的数字以及出现的次数置为 1，直到进行到最后。然后再验证最后留下的数字是否出现次数超过一半，因为可能前面的次数依次抵消掉，最后一个数字就直接是保留下来的数字，但是出现次数不一定超过一半。

[题40-最小的k个数](题40-最小的k个数.py)  
（1）基于划分的方法，**时间复杂度 O(N)** 。需要修改数组。设定一个 key，通过 partion 划分后，比 key 大的数字在右边，小的在左边，返回 left=right d的 left 值。如果 left 比 K 大，在左边寻找最小的 K 个数，反之，则在右边寻找。（2）基于二叉树或者堆来实现，**时间复杂度 O(NlogK)** 。首先把数组前 K 个构建一个最大堆，然后从 K+1 个数字开始遍历数组，如果遍历到的元素小于堆顶的数字，那么交换数字，重新构造堆，继续遍历。

[题41-数据流中的中位数](题41-数据流中的中位数.py)
类似题 40，使用堆实现。构建一个最大堆和一个最小堆，分别存储比中位数小的数和大的数。当目前两堆总数为偶数的时候，把数字存入最大堆，然后重排最大堆，如果最大堆的堆顶数字大于最小堆堆顶数字，则把两个堆顶数字交换，重排两堆，此时两堆数字总数为奇数，直接输出最大堆堆顶数字即为中位数；如果当前两堆总数为技术的时候，把数字存入最小堆，重排最小堆，如果最大堆的堆顶数字大于最小堆堆顶数字，则把两个堆顶数字交换，重排两堆，此时两堆数字总数为偶数，取两堆堆顶数字做平均即为中位数。
