---
title: "26 Remove Duplicates From Sorted Array"
date: "2024-11-12"
categories: ["leetcode", "two-pointers", "array"]
---

Link to the problem: https://leetcode.com/problems/remove-duplicates-from-sorted-array

## Solution 1

This was easier since I got this trick with the slow and quick pointers, where we essentially skip the elements we are not interested in and we swap (or better to say, keep) the elements we are interested in.

Similar to [27 Remove Element](/notes/27-remove-element), but we work with duplicates.

### Code C#

```csharp
public class Solution {
    public int RemoveDuplicates(int[] nums) {
        int previousElement = nums[0]; // nums is not empty
        int keepIndex = 1; // we start with the index 1 since we always keep 0 index
        for (int i = 1; i < nums.Length; i++)
        {
            if (nums[i] != previousElement) // essentially we bypass duplicates and swap not duplicates
            {
                nums[keepIndex] = nums[i];
                previousElement = nums[i];
                keepIndex++;
            }
        }
        return keepIndex;
    }
}
```

### Complexity

- Time O(n)
- Space O(1)