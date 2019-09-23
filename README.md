# 《剑指offer》第二版 Python 实现
[题3.1-找出数组中重复的数字](题3.1-找出数组中重复的数字.py)   
**要求时间复杂度 O(N)，空间复杂度 O(1)** 。因此不能使用排序的方法，也不能使用额外的标记数组。对于这种数组元素在 [0, n-1] 范围内的问题，可以将值为 i 的元素调整到第 i 个位置上进行求解。以 (2, 3, 1, 0, 2, 5) 为例，遍历到位置 4 时，该位置上的数为 2，但是第 2 个位置上已经有一个 2 的值了，因此可以知道 2 重复

[题3.2-不修改数组找出重复的数字](题3.2-不修改数组找出重复的数字.py)   
**时间复杂度 O(NlogN)，空间复杂度 O(1)** 。二分查找方法。以长度为 8 的数组 {2, 3, 5, 4, 3, 2, 6, 7} 为例，那么所有数字都在 1-7 的范围内。中间的数字 4 将 1-7 分为 1-4 和 5-7。统计 1-4 内数字的出现次数，它们一共出现了 5 次，说明 1-4 内必要重复的数字；反之，若小于等于 4 次，则说明 5-7 内必有重复的数字。因为不能使用额外的空间，所以每次统计次数都要重新遍历整个数组一次

[题4-二维数组中的查找](题4-二维数组中的查找.py)
**时间复杂度 O(M+N)** 。从数组右上角或者左下角开始查找array[i][j]

[题5-替换空格](题5-替换空格.py)
**时间复杂度 O(N)** 。如果直接每次遇到空格添加'%20'，那么空格后面的数字就需要频繁向后移动。遇到这种移动问题，可以尝试先遍历一次，找出空格的数量，得到替换后的长度；然后从后往前扫描替换。逆向思维
