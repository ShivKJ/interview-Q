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

### Medium

#### Minimise Cost

There are `n` tasks and cost to complete `ith` task is `costs[i]` where `costs` is array of numbers of size `n`
and `0 <= i < n`.

If first tasks is picked then all the other tasks have to be completed, otherwise at least one of the tasks should be
left. Return an array `x` of numbers, containing `0` or `1` of size `n` where `x[i] = 1` means `ith` task is picked,
such that total cost incurred for picked tasks is minimum.

```python
from typing import List


def min_cost(costs: List[float]) -> List[int]:
    """
    let n = len(costs) and x[i] is binary variable 0 <= i < n

    minimise: sum(costs[i] * x[i] for i in range(n))

    constraint: x[0] = x[1] * x[2] * ... * x[n-1]

    :param costs:
    :return:
    """
    n = len(costs)

    if n < 2:
        raise ValueError(f'number of elements in array can '
                         f'not be less than 2, given array size={n}')

    x = [0] * n
    rest_costs = costs[1:]

    # we branch on the variable x[0]. It can take two values
    # if x = 1
    #   it means x[1], ..., x[n - 1] must all be 1. So objective function
    #   value for this configuration, obj1 = sum(costs)
    obj1 = sum(costs)

    # otherwise (i.e. x = 0),
    #   we need to set value of at least one of the variables to 0 apart from x[0].
    #   But which one to choose?

    #   Defining rest_costs = costs[1:]
    #
    #   As we want to minimise the objective function, so we will want to keep as
    #   many negative numbers, from rest_costs, as possible.
    #
    #   Ofcourse, we can not keep all the numbers from costs, because it will make
    #   solution infeasible. So in case when all the numbers in rest_costs are negative,
    #   then finding the largest cost and setting value for its corresponding variable to 0
    obj2 = sum(c for c in rest_costs if c < 0)
    max_cost_idx_in_rest_costs = None

    if all_negative := all(e < 0 for e in rest_costs):
        max_cost_idx_in_rest_costs = rest_costs.index(max(rest_costs))
        obj2 -= rest_costs[max_cost_idx_in_rest_costs]  # so, x[1 + max_cost_idx_in_rest_costs] = 0
    # ------------------------------------------------------------------------------

    # constructing output
    if obj1 <= obj2:
        # case for x[0] = 1 and hence x[1],...x[n-1] all should be 1
        for i in range(n):
            x[i] = 1
    else:
        # case for x[0] = 0

        for i, c in enumerate(costs):
            x[i] = int(c < 0)

        x[0] = 0

        if all_negative:
            # in the above loop, we will have set x[1:] to 1, which will break
            # feasibility of solution, so setting x[1 + max_cost_idx_in_rest_costs] = 0.
            # (max_cost_idx_in_rest_costs is defined and not None)
            # Note that: we are adding 1 to max_cost_idx_in_rest_costs
            # as max_cost_idx_in_rest_costs is defined in rest_costs array.
            x[1 + max_cost_idx_in_rest_costs] = 0

    return x
```

### Medium

#### [Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)

Given an integer array `nums`, return the length of the longest strictly increasing subsequence.

```
Input: nums = [10,9,2,5,3,7,101,18]
Output: 4
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
```

Solution [link](https://github.com/ShivKJ/practice/blob/master/leetcode/problem300.py)