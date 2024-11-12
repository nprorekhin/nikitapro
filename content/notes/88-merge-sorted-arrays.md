---
title: "88 Merge Sorted Arrays"
date: "2024-11-12"
categories: ["leetcode", "two-pointers", "array"]
---

https://leetcode.com/problems/merge-sorted-array/

## Solution 1

Trick here is to traverse arrays from the end and not from the beginning. Since the maximum number of both arrays will be the last, you can put it to the last element.

### Code C#

```csharp
public class Solution {
    public void Merge(int[] nums1, int m, int[] nums2, int n) {
        var p1 = m - 1;
        var p1Insert = m + n - 1; 
        var p2 = n - 1;

        while(p2 >= 0)
        {
            if (p1 >= 0 && nums1[p1] > nums2[p2])
            {
                nums1[p1Insert] = nums1[p1];
                p1Insert--;
                p1--;
            }
            else
            {
                nums1[p1Insert] = nums2[p2];
                p1Insert--;
                p2--;
            }
        }
    }
}
```

### Complexity

- Time O(m + n)
- Space O(1)