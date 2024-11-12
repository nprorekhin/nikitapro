---
title: "169 Majority Element"
date: "2024-11-12"
categories: ["leetcode", "hash", "ascii"]
---

Link to the problem: https://leetcode.com/problems/majority-element

## Solution 1

My intuition was simple - i use a dictionary (hash map) and just count occurences. I can also compare the maximum number of occurences in place, so I implemented.

### Code C#

```csharp
public class Solution {
    public int MajorityElement(int[] nums) {
        var dict = new Dictionary<int, int>();
        int majorIndex = 0;
        for (int i = 0; i < nums.Length; i++)
        {
            if (!dict.ContainsKey(nums[i]))
            {
                dict[nums[i]] = 0;
            }
            dict[nums[i]]++;
            if (dict[nums[i]] > dict[nums[majorIndex]])
            {
                majorIndex = i;
            }
        }
        return nums[majorIndex];
    }
}
```

### Complexity

- Time O(n)
- Space O(n)


## Solution 2

Later I discovered (in Solution section), that there is a much simpler solution, that relates on the Moore's Voting Algorithm. Believe it or not, you can just work with a simple counter variable. Since the major element will appeear more than n/2 times, it will eventually be captured by this algorithm.

What helped me to grasp the idea better - image you have a sorted array containing [1,1, 1, 1, 1, 2, 2, 3, 3]. In this case you will get the `count` variable equal to 1 and the `majorElement` will be 1. Sweet 🥹!

### Code C#

```csharp
public class Solution {
    public int MajorityElement(int[] nums) {
        int count = 0;
        int majorElement = 0;
        for (int i = 0; i < nums.Length; i++)
        {
            if (count == 0)
            {
                majorElement = nums[i];
            }
            if (majorElement == nums[i])
            {
                count++;
            }
            else
            {
                count--;
            }
        }
        return majorElement;
    }
}
```

### Complexity

- Time O(n)
- Space O(1)