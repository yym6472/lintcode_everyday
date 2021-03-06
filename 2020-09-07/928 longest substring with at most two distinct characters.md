## 题意

- 链接：[https://www.lintcode.com/problem/longest-substring-with-at-most-two-distinct-characters/description](https://www.lintcode.com/problem/longest-substring-with-at-most-two-distinct-characters/description)

这道题的题意为：给定一个字符串，要求找出**最多包含两个不同字符**的最长子串，返回其长度。

## 题解

满足某条件的最长子串和满足某条件的最短子串都可以用双指针来做。以这道题（满足某条件的最长子串）为例：

1. 一开始，两个指针`[a, b]`都指向第一个位置，表示区间`[0, 0]`
2. 右指针先向右移动，移动的过程中维护当前`[a, b]`区间内的字符情况，保证每次维护的复杂度为`O(1)`，同时又能够在`O(1)`的时间复杂度内查询到区间内不同字符的个数
   - 这里的维护方法可以是一个`字符 -> count`的字典，同时使用一个变量保存当前区间内不同字符个数
3. 当右指针移动到`[a, b]`区间内不同字符个数超出2个时，停止移动右指针；转而移动左指针，直到区间内不同字符个数重新回到两个
4. 不断交替上述过程，直到右指针超出边界

其它的题目也是类似，无非维护的状态，以及判断条件根据题意发生了改变。

或者还有可能是从求最长子串变为求最短子串，此时指针移动和上面的流程相反：当满足条件时移动左指针，不满足条件时移动右指针即可。