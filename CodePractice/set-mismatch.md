# Set Mismatch

You have a set of integers s, which originally contains all the numbers from 1 to n. Unfortunately, due to some error, one of the numbers in s got duplicated to another number in the set, which results in repetition of one number and loss of another number.

You are given an integer array nums representing the data status of this set after the error.

Find the number that occurs twice and the number that is missing and return them in the form of an array.

Example 1:

Input: nums = [1,2,2,4]
Output: [2,3]
Example 2:

Input: nums = [1,1]
Output: [1,2]

## My Code
```
public class Solution {
    public int[] FindErrorNums(int[] nums) {
        var errorNums = new List<int>();
        for( int i = 0; i < nums.Length - 1; i++)
        {
            if(nums[i] == nums[i+1])
            {
                errorNums.Add(nums[i]);
                errorNums.Add(nums[i] + 1);
            }
        }

        return errorNums.ToArray();
    }
}
```

## OpenAPI Code
```
public class Solution {
    public int[] FindErrorNums(int[] nums) {
        int n = nums.Length;
        bool[] seen = new bool[n + 1];
        int duplicate = -1, missing = -1;

        foreach (int num in nums)
        {
            if (seen[num])
                duplicate = num;
            seen[num] = true;
        }

        for (int i = 1; i <= n; i++)
        {
            if (!seen[i])
            {
                missing = i;
                break;
            }
        }

        return new int[] { duplicate, missing };
    }
}

```

# Comparison
| Aspect                           | Your Solution | Correct Solution |
| -------------------------------- | ------------- | ---------------- |
| Works when array is unsorted     | ❌             | ✔️               |
| Correct if missing ≠ duplicate+1 | ❌             | ✔️               |
| Handles duplicates not adjacent  | ❌             | ✔️               |
| Time complexity                  | ✔ O(n)        | ✔ O(n)           |
| Space complexity                 | ✔ O(1)/O(n)   | ✔ O(n)           |

 