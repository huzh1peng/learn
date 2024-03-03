# 练功记录

february

| **一** | **二** | **三** | **四** | **五** | **六** | **日** |
| :----: | :----: | :----: | :----: | :----: | :----: | :----: |
|   29   |   30   |   31   | **1**  | **2**  | **3**  | **4**  |
| **5**  | **6**  | **7**  | **8**  | **9**  | **10** | **11** |
| **12** | **13** | **14** | **15** | **16** | **17** | **18** |
| **19** | **20** | **21** | **22** | **23** | **24** | **25** |
| **26** | **27** | **28** | **29** |   1    |   2    |   3    |

march

| **一** | **二** | **三** | **四** | **五** | **六** | **日** |
| :----: | :----: | :----: | :----: | :----: | :----: | :----: |
|   26   |   27   |   28   |   29   | **1**  | **2**  | **3**  |
| **4**  | **5**  | **6**  | **7**  | **8**  | **9**  | **10** |
| **11** | **12** | **13** | **14** | **15** | **16** | **17** |
| **18** | **19** | **20** | **21** | **22** | **23** | **24** |
| **25** | **26** | **27** | **28** | **29** | **30** | **31** |

* 1.29 164m
* 1.30 183m
* 1.31 241m
* 2.1 197m
* 2.3 70m
* 2.6 78m
* 2.7 124m
* 2.14 104m
* 2.15 122m
* 2.16 121m
* 2.17 198m
* 2.18  235m
* 2.19 112m
* 2.20  139m
* 2.21 112m
* 2.22 156m
* 2.23 183m
* 2.26 165m
* 2.27 143m
* 3.1 60m
* total 2742 m 45.7 h

# 字符串

## [Isomorphic Strings 字符串同构](https://leetcode.com/problems/isomorphic-strings/?envType=list&envId=pmpgaryt)

一开始尝试这道题时没有找到很好思路，单纯想着怎么储存各重复字母的所有位置，这是很朴素的想法，实际上记录所有位置是多余的——<font color=red>只需要维护一个记录各个字母上一次出现位置的数组即可</font>。这个数组的长度为255，代表了各个字符。随着遍历整个字符串，保证两个字符串的同位置字母上一次出现的位置相同，遍历完后自然可以保证重复字母的所有位置都相同，比较巧妙。——1.29

## [Palindromic Substrings 回文子串个数](https://leetcode.com/problems/palindromic-substrings/?envType=list&envId=pmpgaryt)

直接按照字串长度进行操作看起来不好，当初我想的是可能用递归的方法来解决。但是怎么把这个问题拆成两个字符串难倒我了，因为不管怎么分，一定是有字串是两头都占的。然后就没有思路。实际上，与其把他分解不如想想怎么生成这样的回文子串。一个回文子串意味着对称，意味着确定中心后向两边延伸左右字符都是一样的，也就是说——<font color=red>遍历这个字符串，把遍历到的字符当成中心向外延伸</font>（长度奇数的直接从中心开始，偶数的从两边开始）就可以遍历所有的可能子串。——1.29

## [Palindrome Number 回文数字](https://leetcode.com/problems/palindrome-number/?envType=list&envId=pmpgaryt)

不将数字转换成字符判断是否回文，我一开始的办法是直接用整除啊求余之类的计算将这个数字颠倒过来。但是这样做比较麻烦。更方便的做法——<font color=red>逐渐生成数字右半部分的颠倒样子，生成右半部分的同时对原数不断除以10得到数字的左半部分</font>。这样方便很多，这样带一些生成的方法思路还是不够熟练啊——1.29

## [Count Binary Substrings 二进制子串个数](https://leetcode.com/problems/count-binary-substrings/?envType=list&envId=pmpgaryt)

这道题我一开始低估了，想用前面计算回文子串个数的方法，遍历一遍字符串，把遍历到的字符为起点延申看能得到几个合格的字串，但是直接超时了。之后观察规则后发现按照这个方法，每一个起点最多只能有一个终点，稍加改进后依然超时。看来需要O(n)的复杂度，事实上我对这题理解还不够深。如果把这样的字串分成前后两块思路就清晰了——<font color=red>满足条件的字串个数完全由后半部分决定，只要后半部分长度小于前半部分，那么总可以在前半部分找到对应起点使字串满足条件的。</font>之后改变数字时只需要让目前的后半部分变成前半部分即可。我太关注于从前往后看再判断合法性，忽略了后半部分的决定作用，而这决定性因素保证了一次遍历就可以完成题目要求。——1.29

# 数组与矩阵

## [Move Zeros 移动零](https://leetcode.com/problems/move-zeroes/description/)

虽然这题很简单，但是没有一次通过。问题出在判断条件上刻舟求剑了，细心一点完全可以避免。——1.30

## [Reshape the Matrix 重塑矩阵](https://leetcode.com/problems/reshape-the-matrix/description/)

这题用的是土味办法，即把原矩阵展开后重新构建新矩阵，思路很简单。其实并不用展开，只需要在构建过程中想办法找到原矩阵对应的元素即可——<font color=red>利用对原矩阵列数整除求余得到目标元素在原矩阵的坐标</font>。这样会方便一些——1.30

## [Max Consecutive Ones 最大连续1的个数](https://leetcode.com/problems/max-consecutive-ones/description/)

这题比较简单，但是做的时候还是犯了错误——更新最大连续个数的代码位置出了问题——1.30

## [Search a 2D Matrix 搜索二维矩阵](https://leetcode.com/problems/search-a-2d-matrix-ii/description/)

这题思路出了问题，一直想着从左上开始慢慢扩展下去，这样子很麻烦。实际上注意到这样类型的矩阵应该从右上角或者左下角入手。拿右上角举例——<font color=red>如果目标比该数字大，那么肯定在这行之下，如果比该数字小，那么肯定在这列之左。</font>——1.30

## [Kth smallest Element in a sorted Matrix 有序矩阵中第k小的元素](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/description/)

这道题完全没思路，想着上一题的思维能不能推出第k小但是失败了。这题的解法有堆解法和二分查找法。我用了最小堆完成，具体思路是——<font color=red>首先将该矩阵的第一列放入这个最小堆中（初始化），然后进行k-1次循环，每次循环取出堆中的最小元素，然后插入这个元素对应矩阵同一行的下一个元素。</font>循环完成后取出堆顶元素即为答案。这里标记一下，等到学完二分查找再回来写二分查找方法——1.30

## [Set Mismatch 被替换的数](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/description/)

这题容易多了，构造一个数组用作次数的映射即可，但是这样空间效率不好。有一次遍历的方法，观察题目得知，当我们得到一个数字时就已经可以确定他的正确位置了（num-1）。因此，<font color=red>遍历数组时考察该元素应在位置上的数字，如果他们相等，那表明该数字就是重复的，否则交换位置，这样遍历下来就能保证数字都在其所在位置上。</font>之后再遍历一遍看那个位置上的数字不对，那么这个位置原来该有的数字就是缺失的那个。关键在于看到了数字和位置的一一对应——1.30

## [Find the Duplicate Number 寻找重复数](https://leetcode.com/problems/find-the-duplicate-number/description/)

这题和上一题的区别是这里的数字可以重复多遍，而且不允许修改原数组，也只能用常数额外空间。有两种思路，一种是二分查找，我放到后面去解决了。这里讲一下使用双指针的解法。<font color=red>把这个数组看成一条路径，对应数字代表着下一个节点。注意到有重复的数字意味着不同位置上的数字可以指向这一个节点，也就意味着有循环出现，而且这个循环开始的节点就是重复数字。</font>因此可以运用双指针来找到这个循环开始的节点，假设在循环开始之前路径长度为$a$，从进入循环到相遇时经过路径$b$，相遇点到循环出口经过$c$。那么在相遇时，慢指针经过路径为$a+b$而快指针经过路径为$a+b+n(b+c)$由于快指针速度是满指针的两倍，因此有$a=c+(n-1)(b+c)$,然后让快指针从头开始和慢指针同步移动，这样当快指针到达循环入口时，也就是移动$a$长度时，慢指针移动了$c+(n-1)(b+c)$长度，正好和快指针相遇，也就找到了循环出口。——1.31

## [Beautiful Arrangement 优美的排列](https://leetcode.com/problems/beautiful-arrangement-ii/description/)

观察到用$k+1$个元素可以完全保证构建出$k$个不同的差值，类似于摆动构建，顺序为$1, k+1, 2, k, 3, k-1...$这样的顺序可以直接满足条件，之后的数字则按照顺序排列即可——1.31

## [Degree of an Array 数组的度](https://leetcode.com/problems/degree-of-an-array/description/)

构建映射，找到出现最多频数的数字们，并且同时保存他们最左和跨度的位置信息，然后比较出最短的就可以，思路很简单。但是需要熟练。——1.31

## [Toeplitz Matrix 托普利茨矩阵](https://leetcode.com/problems/toeplitz-matrix/description/)

只需要遍历并确认和左上角元素是否相等即可，没难度。——1.31

## [Array Nesting 数组嵌套](https://leetcode.com/problems/array-nesting/description/)

这道题的思路和寻找重复数很像，都是把数组看成一条路径，这里要找最长的路径，起初我选择直接全遍历，$O(n^2)$的时间复杂度超时了，其实只需要遍历一遍，遍历每一个节点后都将其设置成-1，代表着已经经历过之后不在考察。因为在一条路径上的点只需要过一遍就行。我一开始还是不太敢直接修改这个数组，其实胆子大点就行。——1.31

## [Max Chunks To Make Sorted 最多能完成排序的块](https://leetcode.com/problems/max-chunks-to-make-sorted/description/)

这题还是蛮有思路的，其实也是运用到了一一对应的思想，要让每一个分块内排序后一一对应，那这个分块内就不可能存在比这个块右边界更大的数，因为如果这种情况发生这个数不可能在这个分块里分配到正确位置。<font color=red>因此我们只需要遍历这个数组一遍，当分块内的数都小于分块最右边界时这样的分块就完成了。</font>——1.31

# 图

## [Is  Graph Bipartite 判断二分图](https://leetcode.com/problems/is-graph-bipartite/description/)

一个图二分，代表这个图可以被两种颜色涂完。所以就转换成了染色问题，在染色问题里自然要记录节点的访问情况，这里不但要分染成两种颜色的哪一种，没上过色又是另一个状态。运用广度优先搜索，对每个未经过染色的相邻节点染上和本节点相反的颜色，如果有相邻节点和本节点颜色一样，则表明这个 染色任务无法完成，图不是二分的。——2.1

## [Course Schedule 课程表](https://leetcode.com/problems/course-schedule/description/)

这题有两个思路，BFS和DFS，用BFS来一遍，那就是倒推一遍，先找到所有不需要前置课程的课（入度为0）加入队列，之后依次取出，相当于学习该课程，之后其相邻节点的入度-1,如果减一后该节点的入度为0，则将这个节点加入队列。环节结束后如果有节点的入度大于0，则表明其有前置课程没满足，不符合题意。——2.1

## [Course Schedule ii 课程表ii](https://leetcode.com/problems/course-schedule-ii/description/)

这题则用DFS思路。首先还是建立一个图，但是和前一道题相反，这道题记录每个节点的先修课程而不是后续课程。在进行DFS时，需要定义一个包含三个状态的visited数组，其等于0表示该节点未被访问过，等于1表示该节点正在访问，等于2表示该节点已经访问。当访问一个节点时，对其先修课程都进行DFS访问确。建立DFS是一个有点爽的过程，他让你看到了解决办法的简洁一面，还是动手实现一遍有感觉。——2.1

## [Redundant Connection 冗余连接](https://leetcode.com/problems/redundant-connection/description/)

这题要使用的时并查集的运用，这种并查集就可以用来判断图中的环，主要不熟悉的是并查集的定义，在这道题目里的应用其实也不复杂。按照顺序归并集合，题目要求的边就是刚加入后产生矛盾的那一条。——2.1

# 位运算

## [Hamming Distance 汉明距离](https://leetcode.com/problems/hamming-distance/)

认识到<font color=red>对两个整数进行异或运算结果的二进制表示中的每个位都表示输入整数对应位的差异</font>；也就是说，如果某个位上的数字相同，则该位为0，如果不同则为1。值得注意的是在位运算中，<font color=red>去掉最低位的1的方法是：$x\&(x-1)$</font>——2.3

## [Single Number 只出现一次的数字](https://leetcode.com/problems/single-number/description/)

需要知道一个性质:<font color=red>成对出现的元素在异或运算中相互抵消</font>。因此只需要将所有元素进行异或运算，最终结果就是那个元素。——2.3

## [Missing Number 丢失的数字](https://leetcode.com/problems/missing-number/description/)

逆向思维，如果<font color=red>把0到n这n+1个数字和数组里的数字都做异或运算</font>，成对抵消剩下的就是丢失的数字。——2.3

## [Single Numberiii 只出现一次的数字III](https://leetcode.com/problems/single-number-iii/description/)

这次如果对所有数字取异或得到的值是两个不同值的异或结果，要想办法分离他们。首先找到这个结果中的某一个1，因为这个1代表着这两个值不一样的地方。<font color=red>在实际过程使用了$x \& -x$ 这个方法，这个方法可以找到x最低位的1，之后再对原数组进行遍历，按照这个位置是0或者1分成两组，每组均对组内所有成员求异或，得到的两个值即为答案。</font>值得注意的是在尝试对‘int’取负操作时，又可能会结果溢出，应当改为无符号数unsigned int。——2.3

## [Reverse Bits 颠倒二进制位](https://leetcode.com/problems/reverse-bits/description/)

思路是每次取出原有数字的最后一位然后添加到结果中。如何添加？用`result |= (n & 1)` 即可。——2.6

## [Power of  Two 二的幂](https://leetcode.com/problems/power-of-two/description/)

一个数是二的幂代表着二进制表示只有一个1，c++中用 `__builtin_popcount(n)`表示n的二进制中有多少个1。——2.6

## [Power of four 四的幂](https://leetcode.com/problems/power-of-four/description/)

四的幂表示二进制中只有一个1且为奇数位。要判断这个1是否在奇数位，可以使用一个只有奇数位上有1的掩码进行位于操作。（注意在进行位操作并判断时正确使用括号）——2.6

## [Binary Number with Alternating Bits 交替位二进制数](https://leetcode.com/problems/binary-number-with-alternating-bits/description/)

交替位二进制数特点是和右移一位的数每一位都不一样，结果全是1。判断一个二进制数是不是全是1，和这个数加一做位与操作即可。——2.6

## [Number Complement 数字的补数](https://leetcode.com/problems/number-complement/description/)

只要得到与该数字等长的全为1的掩码，让该数字和掩码做异或运算即可。——2.6

## [Sum of Two Integers 两整数之和](https://leetcode.com/problems/sum-of-two-integers/description/)

理解`a ^ b`相当于没有进位的两数和，而`(a & b) << 1`则为进位数字。——2.6

## [Maximum Product of Word Lengths 最大单词长度乘积](https://leetcode.com/problems/maximum-product-of-word-lengths/description/)

将单词转换成一个32位的二进制数：`mask[i] |= (1 << (c - 'a'))`之后只要进行位与操作就可以判断是否有重复。——2.6

## [Counting Bits 比特位计数](https://leetcode.com/problems/counting-bits/description/)

如果x是偶数，则1的数量与x/2中1的数量相同，如果是奇数，则比x-1中1的数量多1。——2.6

# 排序

## [Kth Largest Element in an Array 数组中的第K个最大元素](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)

topk问题，第一种直接用堆的方法，维护一个size为k的最小堆即可。第二种方法是快速选择，类似于快排设置一个pivot然后分治。——2.7

## [Top K Frequent Element 前k个高频元素](https://leetcode.com/problems/top-k-frequent-elements/description/)

topk直接让人联想到堆，也可以用桶排序法，先建立frequencymap，然后把相同频率的元素装在一个桶内，要取前k个就从后往前数即可。——2.7

## [Sort Characters By Frequency 根据字符出现频率排序](https://leetcode.com/problems/sort-characters-by-frequency/description/)

同上。——2.7

## [Sort Colors 颜色分类](https://leetcode.com/problems/sort-colors/description/)

这题遍历一遍即可，方法是荷兰国旗问题的三向划分法。使用三个指针（low, mid, high）分别跟踪数组中的三种元素。目标是把所有的0移到前面，2移到后面。用mid对数组遍历，如果遇到0，则将其与low指向元素对换，然后将low和mid都往前移动一步；如果遇到1，则将mid往前移动一步；如果遇到2，则将其与high指向元素对换，然后将high往后退一步。——2.7

# 贪心

## [Assign Cookies 分发饼干](https://leetcode.com/problems/assign-cookies/description/)

简单，将两个数组倒序排列后按照顺序分发。即先满足最大需求的确保不浪费。——2.14

## [Non-overlapping Intervals 无重叠区间](https://leetcode.com/problems/non-overlapping-intervals/description/)

简单，先按照右边界升序排列，再考察是否重叠。——2.14

## [Minimum Number of Arrows to burst Ballons 用最少数量的箭引爆气球](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/)

简单，先按照左边界升序排列，再考察是否重叠并维护一个重叠边界，超出这个重叠边界则需要加一个箭。——2.14

## [Queue Reconstruction by height 根据身高重建队列](https://leetcode.com/problems/queue-reconstruction-by-height/description/)

中等，先按照身高降序，再按照k升序，之后按照k位置逐个插入队伍即可。——2.14

## [Best Time to Buy and Sell Stock 买卖股票的最佳时机](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

简单，维护一个股票的最低价格，遍历数组在每个时机计算利润。——2.14

## [Best Time to Buy and Sell Stock 买卖股票的最佳时机 II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/)

简单，当当前价格高于前一天价格时卖出再买入即可。——2.14

##  [Can Place Flowers 种花问题](https://leetcode.com/problems/can-place-flowers/description/)

简单，设置状态2为间隔。遍历，如果该位置为0且两边没有1，即代表可以种，且将两边都设置为2，如果该位置为1，则将两边设置成2。——2.14

## [Is Subsequence 判断子序列](https://leetcode.com/problems/is-subsequence/description/)

双指针轻松解决。——2.15

## [Non-decreasing Array 非递减数列](https://leetcode.com/problems/non-decreasing-array/description/)

中等，遍历数组，如果出现了递减的情况，则需要考虑让该元素变小或是让后一个元素变大。这里用到了贪心思想——我们应当尽可能让这个元素变小，因为如果让后一个元素变大，则会对后续继续造成压力。可是如果该元素的前一个元素大于后一个元素，我们只能让后一个元素变大。——2.15

## [Maximum Subarray 最大子数组和](https://leetcode.com/problems/maximum-subarray/description/)

简单，遍历然后判断是否新开子数组或是继续加上。——2.15

## [Partition Labels 划分字母区间](https://leetcode.com/problems/partition-labels/description/)

中等，首先遍历数组，得到每个字符最右边的index。再遍历一次，维护一个begin和end，当遍历到的index==end时划分区间。——2.15

# 二分查找

## [Sqrt(x) x的平方根](https://leetcode.com/problems/sqrtx/description/)

题目本身思路简单，但是要写的clean一些不简单。——2.15

## [Find Smallest Letter Greater Than Target 寻找比目标字母大的最小字母](https://leetcode.com/problems/find-smallest-letter-greater-than-target/description/)

虽然同样不难，但在写二分查找时总感觉不得劲，生怕边界出问题。——2.15

## [Single Element in a Sorted Array 有序数组中的单一元素](https://leetcode.com/problems/single-element-in-a-sorted-array/description/)

有点难，要考虑单个元素前后两端的差别，首先这个元素一定出现在偶数index上，所以可以只考察偶数index。当nums[m] == nums[m + 1]情况时则表示m在待寻找元素前面，反之后面。——2.16

## [First Bad Version 第一个错误的版本](https://leetcode.com/problems/first-bad-version/description/)

秒杀。——2.16

## [Find Minimum in Rotated Sorted Array 寻找旋转排序数组中的最小值](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/)

简单，很公式的二分查找，就是很直觉地找出前后区别。——2.16

## [Find First and Last Position of Element in sorted Array 在排序数组中查找元素的第一个和最后一个位置](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/)

难！这题的思路是找到目标数出现的左界，至于右界则为目标数加1的左界减1。但是问题是在之前的二分查找中因为惯性思维直接将h设置成了size-1。但是在这题需要设置成size。因为如果target+1超出了数组的上界，我们无法得到最后正确的右界size-1。因为常规的二分查找将搜索区间限定在了[0,size),而现在我们需要扩大这个区间。——2.16

# 分治

## [Different Ways to Add Parentheses 为运算表达式设计优先级](https://leetcode.com/problems/different-ways-to-add-parentheses/description/)

中等，单纯利用分治思想，很好的入门题。——2.16

## [Unique Binary Search Trees II 不同的二叉搜索树](https://leetcode.com/problems/unique-binary-search-trees-ii/description/)

有点难，主要是目前为止对分治还没有很熟。包括很多细节。但本质上还是递归咯——2.16

# 搜索

## [Shortest Path in Binary Matrix 二进制矩阵中的最短路径](https://leetcode.com/problems/shortest-path-in-binary-matrix/description/)

中等，要考虑到bfs的所有细节，具体思路是先初始化队列存储访问路径，然后初始化将起点加入队列。只要队列不为空，那么对当前的层次size进行遍历，这一步的出发点是知道路径的长度，即遍历完这一层次，path length++。在遍历过程中，取出第一个元素，如果到达了终点，则直接返回路径长度，反之将其可能经过的(原来grid为0的)点都加入队列，之后将该元素的grid设置成一。(不能忘记边界检查)。属于是bfs的公式。——2.17

## [Perfect Squares 完全平方数](https://leetcode.com/problems/perfect-squares/description/)

中等，知道上一题怎么做后完全是依葫芦画瓢的操作。但是要心里有数这是搜索问题。——2.17

## [Word Ladder 单词接龙](https://leetcode.com/problems/word-ladder/description/)

难，按照公式做法我超时了。原因是我执着于遍历数组后比较，但是这个字典数组太长了。正确做法是先建立一个包含了所有单词的字典，之后遍历所有可能的单字母变化单词，并在这个unordered_set里查找是否存在，若存在则push并且在字典里删除（表示已经访问）。——2.17

## [Max Area of Island 岛屿的最大面积](https://leetcode.com/problems/max-area-of-island/description/)

中等，是dfs搜索的公式级别题目。——2.17

## [Number if Islands 岛屿数量](https://leetcode.com/problems/number-of-islands/description/)

中等，纯公式。——2.17

## [Number of Provinces 省份数量](https://leetcode.com/problems/number-of-provinces/)

偏难，在公式的基础上需要动动脑子，把isConnected [i] [i] 当作visited [i]来使用，如果访问到的边是1且两个端点都没有访问过，则dfs下一个点。——2.17

## [Surrounded Regions 被围绕的区域](https://leetcode.com/problems/surrounded-regions/description/)

难，要考虑到需要从边界入手进行dfs，不是公式。——2.18

## [Pacific Atlantic Water FLow 太平洋大西洋水流问题](https://leetcode.com/problems/pacific-atlantic-water-flow/description/)

难，和上一题一样，很难解决visited的问题，要从边界入手，并且要处理很多细节，不公式，值得反复练习。——2.18

## [Letter Combinations of a Phone Number 电话号码的字母组合](https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/)

中等，回溯的公式题。——2.18

## [Restore IP Addresses 复原IP地址](https://leetcode.com/problems/restore-ip-addresses/description/)

较难，主要是没有清晰的思路。看来目前对回溯还不熟练。这题在边界处理还有一些细节没有处理好。(在选择下一个segment时要考虑有没有超出原有字符串的长度范围)——2.18

## [Word Search 单词搜索](https://leetcode.com/problems/word-search/description/)

较难，按照公式做法确实可以做出来，但是有点太慢了。一个非常大的优化策略是：对board中的字符频率进行检查，如果有字符在board中的频率低于在word中的频率，则直接return false。——2.18

## [Binary Tree Paths 二叉树的所有路径](https://leetcode.com/problems/binary-tree-paths/description/)

比较简单,纯公式,但依旧要注意细节。——2.18

## [Permutations 全排列](https://leetcode.com/problems/permutations/description/)

中等公式题，就是回溯时用vector.pop_back()要注意了。——2.19

## [Permutations II 全排列 II](https://leetcode.com/problems/permutations-ii/description/)

难，难点在于怎么避免重复路径，思路是先排序，保证重复数字在一块。<font color=red>然后再dfs的过程中判断当前元素是否和前一个元素相等，如果相等且前一个元素未访问过，则跳过当前元素。这是因为如果访问了这个元素，本质上和访问前一个元素但没访问当前元素的状态是一样的，然而这个状态已经在之前出现过，所以避免重复复跳过。</font>——2.19

## [Combinations 组合](https://leetcode.com/problems/combinations/description/)

中等，公式题，唯一的细节是要在回溯函数里加入start参数为了避免组合回头重复，要像火车一样一路开向前。——2.19

## [Combination Sum 组合总和](https://leetcode.com/problems/combination-sum/description/)

中等，和上一题一样的思路，避免重复。——2.19

## [Combination Sum II 组合求和 II](https://leetcode.com/problems/combination-sum-ii/description/)

难，我按照惯性思维设置了vis,事实上并不需要。并且<font color=red>判断条件也与全排列II有些许不同：i > start && candidates[i] == candidates[i - 1]。</font>但是原理和思路都是类似的。——2.19

## [Combination Sum III 组合综合III](https://leetcode.com/problems/combination-sum-iii/description/)

中等，公式。——2.19

## [Subsets 子集](https://leetcode.com/problems/subsets/description/)

中等，公式。——2.20

## [Subsets II 子集II](https://leetcode.com/problems/subsets-ii/description/)

偏难，依旧是运用到了避免重复的算法，但是我一开始是设置了一个len来判断是否完成dfs并且加入ans中，但实际上是多此一举，因为在dfs过程中的每一个路径都是要求的子集！——2.20

## [Palindrome Partitioning 分割回文串](https://leetcode.com/problems/palindrome-partitioning/description/)

中等，现在回溯的公式越看越土。——2.20

## [Sudoku Solver 解数独](https://leetcode.com/problems/sudoku-solver/description/)

难题，这题第一麻烦在于判断合法性，我一开始写的太啰嗦了，实际上放进一个0-9的循环就可以把行列方块三种情况都判断了。第二麻烦在于回溯要提前终止，原先的公式都是用一个ans储存结果，但是这道题需要直接在board上操作，为了避免后续的dfs继续错误修改board，要利用bool dfs灵活的终止所有的dfs！这也是新公式。——2.20

## [N-queens N 皇后](https://leetcode.com/problems/n-queens/description/)

难题，但是做完解数独后就是一遍过的程度^^。——2.20

# 动态规划

## [Climbing Stairs 爬楼梯](https://leetcode.com/problems/climbing-stairs/description/)

中等，斐波那契数列，dp[i] = dp[i - 1] + dp[i - 2] 。——2.21

## [House Robber 打家劫舍](https://leetcode.com/problems/house-robber/description/)

中等，dp[i]表示到第i个房子能偷到的最大金额，那么对于某间房子i,如果偷，则得到dp[i - 2] + nums[i]；如果不偷，则得到dp[i - 1]，因此状态转移方程dp[i] = max(dp[i - 2] + nums[i], dp[i - 1]) 。——2.21

## [House Robber II 打家劫舍 II](https://leetcode.com/problems/house-robber-ii/description/)

偏难，变成环后思路没了。实际上这个问题需要进一步细分。因为如果偷了第一个房子，那么就不能偷最后一个房子，以此为分界，这个问题可以分解成两个子问题。一是考虑偷第一个房子，那么就变成第一个房子到倒数第二个房子的线性问题；二是不偷第一个房子，那么就变成了第二个房子到最后一个房子的线性问题。——2.21

## [Minimum Path Sum 最小路劲和](https://leetcode.com/problems/minimum-path-sum/description/)

中等，思路很直观，但是要首先处理第一行和第一列。——2.21

## [Unique Paths 不同路径](https://leetcode.com/problems/unique-paths/description/)

简单，基本秒杀，但是有个细节可以优化：在初始化的时候直接将grid所有位置设置成1，并不需要先处理第一行和第一列。——2.22

## [Range Sum Query - Immutable 区域和检索 - 数组不可变](https://leetcode.com/problems/range-sum-query-immutable/description/)

中等，思路不难，但是值得一试。——2.22

## [Arithmetic Slices 等差数列划分](https://leetcode.com/problems/arithmetic-slices/description/)

难，没有思路。这题巧妙在定义dp[i]是以第i个数字结尾的等差数列总数，而我之前纠结于让这个dp表示所有子等差数列总数。按照新思路如果nums[i] - nums[i - 1] == nums[i - 1] - nums[i - 2]那么dp[i] = dp[i - 1] + 1,只是多了一个i - 2, i - 1, i构成的数列。——2.21

## [Integer Break 整数拆分](https://leetcode.com/problems/integer-break/description/)

中等，思路是这样的：对于遍历到的i,对j从1到i-1遍历，相当于从i中拆分出一个数，因此有状态转移方程dp[i] = max(dp[i], max(j * (i-j), j * dp[i-j]))。——2.21

## [Perfect Squares 完全平方数](https://leetcode.com/problems/perfect-squares/description/)

中等，在之前bfs时做过，但是这次见到对bfs印象又淡了。。。现在记性这么差了吗。。但是按照dp的思路更加清晰了，与Integer Break基本一样。但是！按照这个方法实在是太慢了。换个思路，对于每一个i,考虑所有可能的j，观察是否可以将j * j作为最后一个数字加到i上，因此状态转移方程为dp[i] = min(dp[i], dp[i - j * j] + 1)——2.22

## [Decode Ways 解码方法](https://leetcode.com/problems/decode-ways/description/)

中等，思路比较直观。但是我的判断逻辑有些繁琐了。可以简化。——2.22

## [Longest Increasing Subsequence 最长递增子序列](https://leetcode.com/problems/longest-increasing-subsequence/description/)

难，使用基础dp的时间复杂度为O(n^2)，需要优化。思路是维护一个tails数组，tails[i]表示长度为i+1的递增子序列末位数的最小值，显然这个数组是递增的（长度长的递增子序列肯定比长度短的末尾数大）。在遍历nums的过程中，对这个tails做二分查找，找到一个大于等于nums[i]的位置，这表明可以用nums[i]更新tails。如果没有找到，则表明递增子序列可以加1，直接把nums[i]加入tails末尾即可。最后返回tails的size。——2.22

## [Maxinum Length of Pair Chain 最长数对链](https://leetcode.com/problems/maximum-length-of-pair-chain/description/)

中等，和Longest Increasing Subsequence 类似的维护一个tails数组使时间复杂度为O(nlongn)。——2.22

## [Wiggle Subsequence 摆动序列](https://leetcode.com/problems/wiggle-subsequence/description/)

难，要求是时间复杂度为O(n)，<font color=red>这里设置两个变量up和down，分别表示最后一个摆动是上升或下降的序列长度，之后遍历数组，如果当前元素大于前一个元素，则up = down + 1可以理解为再之前最后一个摆动为下降的序列后面加一个上升的摆动。反之道理雷同，down = up + 1。</font>——2.23

## [Longest Common Subsequence 最长公共子序列](https://leetcode.com/problems/longest-common-subsequence/description/)

难，要用一个二维数组来dp，其中dp[ i ]\[ j ]表示S1的前i个字符与S2的前j个字符最长公共子序列的长度，考虑S1\_i与S2\_ j的值是否相等，分成两种情况

* 当两者相等时，那么可以在S1的前i-1个字符和S2的前j-1个字符最长公共子序列的基础上再加上这个值。最长公共子序列长度加1，即dp[i]\[j] = dp[i - 1]\[j - 1] + 1
* 两者不相等，此时最长公共子序列为S1的前i-1个字符和S2的前j个字符的最长公共子序列，或者是S1的前i个字符和S2的前j-1个字符的最长公共子序列，取他们的最大值，即dp[i]\[j] = max(dp[i - 1]\[j, dp[i]\[j - 1])。——2.23

## 01背包问题

普通二维数组dp，dp[i]\[j]表示前i个物品体积不超过j的情况下能达到的最大价值，也就是用一个容积为j的包去装前i个物品所能达到的最大值。分两种情况(w[i], v[i]分别代表第i件物品体积和价值)：

* 没有选择第i件物品，那么dp[i]\[j] = dp[i - 1]\[j]
* 选择了第i件物品，那么dp[i]\[j] = dp[i - 1]\[j - w[i]] + v[i]

可以对上述式子进行优化，可以看到这个dp数组的每一行完全依赖上一行完成，对两行之前的数据无关，所以可以压缩成一行的dp，每次取第i个物品时进行更新。因此有

* dp[j] = max (dp[j], dp[j - w[i]] + v[i])。

<font color=red>重要的是，这种方法进行更新需要注意更新顺序</font>，在确定第i件物品遍历j即背包容积(内循环)的过程中，应当从大到小逆序遍历，这是因为在原先的设想中，这一行的数据是由上一行来更新的，也就是不考虑物品i，但是如果从小到大遍历，在背包容积比较小的时候会将物品i纳入其中，那么在遍历到背包容积比较大的时候所采用的数据则是考虑到物品i的，即被更新过的，这样是错误的。而从大到小的遍历方式可以避免。——2.23

## [Partition Equal Subset Sum 分割等和子集](https://leetcode.com/problems/partition-equal-subset-sum/)

中等，本质上是一个sum / 2容量01背包问题。——2.23

## [Target Sum 目标和](https://leetcode.com/problems/target-sum/description/)

难，要有转换的思路。记P为所有符号为正的数，N为所有符号为负的数。则有：

* sum(P) + sum(N) = sum(nums)
* sum(P) - sum(N) = target
* sum(P) = (sum(nums) + target) / 2

转换成求特定和子集问题。——2.23

## [Ones and Zeros 一和零](https://leetcode.com/problems/ones-and-zeroes/description/)

中等，需要有一个二维的dp，但思路大差不大。——2.23

## [Coin Change 零钱兑换](https://leetcode.com/problems/coin-change/description/)

中等，这题允许重复属于完全背包问题，也就是说是01背包问题优化版的逆序遍历，即在更新当前状态时不需要保证在前一个状态基础上更新，内外循环都正序遍历即可。——2.26

## [Coin Change II 零钱兑换 II](https://leetcode.com/problems/coin-change-ii/description/)

中等，思路类似只是状态转移方程有一点点不同。——2.26

## [Word Break 单词拆分](https://leetcode.com/problems/word-break/description/)

有点难，不是很公式，由于惯性思维，我的出发点局限在了给定的dict上，但是这题从整个字符串入手考虑dp更好。因为这是需要考虑顺序的背包问题，也就是说单词要按照一定顺序放入背包，这样的问题需要将背包的迭代放在外层。定义布尔型dp，dp[i]表示字符串的前i个字符能够被dict中的单词完全分割。遍历i,对每个i遍历所有的分割点j，如果dp[j] == true 且s[j, i-1]在dict中，则dp[i] = true。——2.26

## [Combination Sum IV 组合总和](https://leetcode.com/problems/combination-sum-iv/description/)

有点难，属于涉及顺序的完全背包问题，外层为背包迭代，内层为顺序遍历。但是具体做的时候边界细节没考虑周全。——2.26

## [Best Time to Buy and Sell Stock with Cooldown 买卖股票的最佳时机含冷冻期](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/)

难，需要考虑三种状态：hold, cooldown, nothold.每种状态都有各自的状态转移方程。——2.26

## [Best Time to Buy and Sell Stock with Transaction Fee 买卖股票的最佳时机含手续费](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/description/)

中等，掌握了如何分类状态，就成了秒杀题目。——2.26

## [Best Time to Buy and Sell Stock III 买卖股票的最佳时机 III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/submissions/1187683094/)

中等，四个状态，buy1, sell1, buy2, sell2。——2.27

## [Best Time to Buy and Sell Stock IV 买卖股票的最佳时机IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/)

难，需要用数组存储状态并且维护。buy[i]数组表示对第i次买入时的最大利润，sell[i]数组表示对第i次卖出时的最大利润。——2.27

## [Delete Operation for Two Strings 两个字符串的删除操作](https://leetcode.com/problems/delete-operation-for-two-strings/description/)

难，相当于是求两个字符串的最长公共子序列，前不久刚做过。——2.27

## [Edit Distance 编辑距离](https://leetcode.com/problems/edit-distance/description/)

难，思路需要一点变通。同样构造一个二维的dp[i]\[j]代表第一个字符串的前i个字符与第二个字符串的前j个字符的编辑距离，之后初始化。然后遍历：

* 当word1[i - 1] == word2[j - 1]时，可以看作这两个字符串在长度分别为i - 1, j - 1的基础上均多出来一个相同的字符，而这个字符不需要编辑，所以dp[i]\[j] = dp[i - 1]\[j - 1]
* 当word1[i - 1] != word2[j - 1]时，这里不仅仅需要考虑dp[i]\[j] = dp[i - 1]\[j - 1] + 1的问题了，因为如果这两个字符串的前一个字符是相等的话，举个例子 ho 和hos，明显应该直接插入s而不是在h和ho的基础上替换。因此dp[i]\[j] = 1 + min({dp[i - 1]\[j - 1], dp[i - 1]\[j], dp[i]\[j - 1]})

——2.27

## [2 Keys Keyboard 两个键的键盘](https://leetcode.com/problems/2-keys-keyboard/description/)

中等，不能忽略复制也算一次操作。——2.27

# 数学

## [Count Primes 计数质数](https://leetcode.com/problems/count-primes/description/)

中等，使用著名的Sieve of Eratosthenes算法，基本思想是从最小的质数2开始，逐步筛选掉每个指数的倍数即可。——2.27

## [Base 7 七进制数](https://leetcode.com/problems/base-7/description/)

简单。就是要注意字符串的用法。——3.1

## [Convert a Number to Hexadecimal 数字转换为十六进制数](https://leetcode.com/problems/convert-a-number-to-hexadecimal/description/)

中等，需要对进制和位运算熟悉。——3.1

## [Excel Sheet Column Title Excel表列名称](https://leetcode.com/problems/excel-sheet-column-title/description/)

中等，相当于转化成二十六进制。——3.1
