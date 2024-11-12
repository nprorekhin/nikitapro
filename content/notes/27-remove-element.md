---
title: "27 Remove Element"
date: "2024-11-12"
categories: ["leetcode", "two-pointers", "array"]
---

Link to the problem: https://leetcode.com/problems/remove-element

## Solution 1

I solved it using the swap idea and two pointers going from beginning and from the end. 
My solution is ok on speed and space, but there is a more elegant solution to this, when you actually swap the "not equal" elements and skip "equal". See the Solution 2.

### Code C#

```csharp
public class Solution {
    public int RemoveElement(int[] nums, int val) {
        int p1 = 0;
        int p2 = nums.Length - 1;
        int counts = 0;
        while(p1 <= p2)
        {
            if (nums[p1] == val)
            {
                if (nums[p2] != val)
                {
                    (nums[p1], nums[p2]) = (nums[p2], nums[p1]);
                    counts++;
                    p1++;
                    p2--;
                }
                else
                {
                    counts++;
                    p2--;
                }
            }
            else
            {
                p1++;
            }
        }
        return nums.Length - counts;
    }
}
```

### Complexity

- Time O(n)
- Space O(1)

## Solution 2

Idea is simple. You have two pointers running from the beginning. One being "fast" (for comparing) and one being "slow" (for keeping the values). You iterate over array with the slow pointer and if the value is not equal to the removal value, you put into slow pointer slot. Otherwise you skip.

### Code C#

```csharp
public class Solution {
    public int RemoveElement(int[] nums, int val) {
        int keepIndex = 0;
        for (int i = 0; i < nums.Length; i++)
        {
            if (nums[i] != val) // we keep the number
            {
                nums[keepIndex] = nums[i];
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