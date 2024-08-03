# [1460. Make Two Arrays Equal by Reversing Subarrays](https://leetcode.com/problems/make-two-arrays-equal-by-reversing-subarrays/)

You are given two integer arrays of equal length <code>target</code> and <code>arr</code>. In one step, you can select any non-empty subarray of <code>arr</code> and reverse it. You are allowed to make any number of steps.

Return <code>true</code> if you can make <code>arr</code> equal to <code>target </code>or <code>false</code> otherwise.

**Constraints**:

* <code>target.length == arr.length</code>
* <code>1 <= target.length <= 1000</code>
* <code>1 <= target[i] <= 1000</code>
* <code>1 <= arr[i] <= 1000</code>

**Similar Questions**:

* [Count Pairs Whose Sum is Less than Target](https://leetcode.com/problems/count-pairs-whose-sum-is-less-than-target)


# Solution C++

```cpp
// Space: O(1)  - count array has length 1001.
//              - Using a vector<int> of length arr.length would save a little memory but
//                it would also be slower since memory would have to be allocated on
//                the heap instead of the stack.
// Time:  O(1)  - Since both arrays have length <= 1000, the 3 for() loops will
//                do <= 1000 + 1000 + 1001 = 3001 iterations combined.
//              - A different (O(N) run-time solution) would be needed if the 
//                lengths and values of the arrays were not bounded above by 1000.

class Solution {
public:
    bool canBeEqual(vector<int>& target, vector<int>& arr) {
        int count[1001] = {}; // Initialize to 0
        for (auto x : arr) count[x]++;
        for (auto x : target) count[x]--;
        for (auto x : count)
            if (x != 0) return false;
        return true;
    }
};
```
