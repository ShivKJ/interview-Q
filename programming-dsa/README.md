# Data Structure & Algorithm

## Coding

### Easy

#### [Combination Sum](https://leetcode.com/problems/combination-sum/)

Given an array of distinct integers candidates and a target integer `target`, return a list of all unique combinations
of candidates where the chosen numbers sum to target.

The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the frequency
of at least one of the chosen numbers is different.

```
Input: candidates = [2,3,6,7], target = 7
Output: [[2,2,3],[7]]
Explanation:
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.
```

```
Input: candidates = [2,3,5], target = 8
Output: [[2,2,2,2],[2,3,3],[3,5]]
```

```
Input: candidates = [2], target = 1
Output: []
```

Solution [link](https://github.com/ShivKJ/practice/blob/master/leetcode/problem39.py).

#### [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum
and return its sum.

A subarray is a contiguous part of an array.

```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

Solution [link](https://github.com/ShivKJ/practice/blob/master/leetcode/problem53.py).

#### [Merge Intervals](https://leetcode.com/problems/merge-intervals/)

Given an array of `intervals`, merge all overlapping intervals, and return an array of the non-overlapping intervals
that cover all the intervals in the input.

Each item in array `intervals` is list of numbers size 2 where first number represents start and second number
represents end of interval.

```
Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].
```

```
Input: intervals = [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considered overlapping.
```

**Note:** array `intervals` will have length at least 1.

Solution [link](https://github.com/ShivKJ/practice/blob/master/leetcode/problem56.py).