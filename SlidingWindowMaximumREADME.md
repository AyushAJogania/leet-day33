# leet-day33

# Sliding Window Maximum

## Problem Statement

You are given an array of integers `nums` and an integer `k`. There is a sliding window of size `k` which is moving from the very left of the array to the very right. You can only see the `k` numbers in the window. Each time the sliding window moves right by one position, you need to return the maximum element in the current window.

## Example

### Input

```
nums = [1,3,-1,-3,5,3,6,7], k = 3
```

### Output

```
[3,3,5,5,6,7]
```

## Approach

To solve this problem, we can use a double-ended queue (deque) to store the indices of elements in the current window. The deque will store elements in descending order of their values, and it will help us keep track of the maximum element in the window efficiently.

Here's how we can approach the problem:

1. Initialize an empty deque `dq` and an empty result vector `result`.
2. Iterate through the array `nums` using the index `i` from `0` to `n-1`, where `n` is the size of the array.
3. Remove the indices from the front of `dq` that are no longer in the current window (i.e., outside the range `[i-k+1, i]`).
4. Remove the indices from the back of `dq` that have values smaller than the current element `nums[i]`.
5. Append the index `i` to the back of `dq`.
6. If `i` is greater than or equal to `k-1`, then the front of `dq` contains the maximum element in the current window. Append it to the `result` vector.
7. Return the `result` vector.

## Complexity Analysis

- Time complexity: O(n), where n is the number of elements in the array.
- Space complexity: O(k), as the maximum size of the deque can be `k`.

## Implementation

Here's the implementation of the approach in C++:

```cpp
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        deque<int> dq;
        vector<int> result;
        
        for (int i = 0; i < nums.size(); i++) {
            // Remove indices that are outside the current window
            if (!dq.empty() && dq.front() < i - k + 1) {
                dq.pop_front();
            }
            
            // Remove indices of elements smaller than nums[i]
            while (!dq.empty() && nums[dq.back()] < nums[i]) {
                dq.pop_back();
            }
            
            dq.push_back(i);
            
            // If window size is reached, add maximum element to result
            if (i >= k - 1) {
                result.push_back(nums[dq.front()]);
            }
        }
        
        return result;
    }
};
```

## Conclusion

Using a deque to maintain the indices of elements in the sliding window helps us efficiently find the maximum element in each window. The provided C++ solution demonstrates this approach, providing an efficient solution to the problem.
