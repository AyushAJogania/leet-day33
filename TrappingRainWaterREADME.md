# leet-day33

# Trapping Rain Water

Given an array `height` representing the heights of bars in an elevation map, the task is to calculate the amount of water that can be trapped after raining.

## Problem Description

You are given an array `height`, where each element `height[i]` represents the height of a bar at position `i`. The width of each bar is 1. The objective is to calculate the total trapped water between the bars after it rains.

## Example

### Input
```cpp
height = [0,1,0,2,1,0,1,3,2,1,2,1]
```

### Output
```
6
```

Explanation: The elevation map can be visualized as follows:

```
   #
#  ## #
## ## ##
012345678901
```

The water trapped at positions 2, 4, 5, 6, 8, and 10 is a total of 6 units.

## Approach

The approach to solving this problem involves calculating the maximum heights to the left and right of each position. This is done using two arrays `left_max` and `right_max`. After precalculating these arrays, we iterate through the `height` array and calculate the trapped water at each position as the minimum of `left_max` and `right_max` at that position minus the current `height`.

## Implementation

1. Declare a class named `Solution`.
2. Define a member function `trap` that takes a vector of integers `height` as input and returns an integer.
3. Inside the `trap` function:
   - Get the size of the `height` array (`n`).
   - Declare two arrays `left_max` and `right_max`, each of size `n`, to store the maximum heights to the left and right of each element.
   - Calculate `left_max` array using a loop.
   - Calculate `right_max` array using a loop.
   - Initialize a variable `water` to keep track of trapped water.
   - Iterate through the `height` array:
     - Calculate trapped water at the current position using `min(left_max[i], right_max[i]) - height[i]`.
     - If the trapped water is greater than 0, add it to the `water` variable.
   - Return the final value of `water`, which represents the total trapped water.

## Complexity Analysis

- Time complexity: O(n), where n is the size of the input array `height`. We iterate through the array twice to calculate `left_max` and `right_max`, and then iterate once more to calculate the trapped water.
- Space complexity: O(n), as we use additional arrays `left_max` and `right_max` of the same size as the input array.

## Conclusion

The "Trapping Rain Water" problem involves efficiently calculating the amount of water trapped between bars in an elevation map after raining. By precalculating the maximum heights to the left and right of each position, we can optimize the computation of trapped water for each position. This solution provides an efficient approach to solving the problem and can handle large input arrays.
