# maximum number of consecutive 1's in the array

Given a binary array nums, return the maximum number of consecutive 1's in the array.


Example 1:

Input: nums = [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s. The maximum number of consecutive 1s is 3.
Example 2:

Input: nums = [1,0,1,1,0,1]
Output: 2

## My Code
```
 
public class Solution {
    public int FindMaxConsecutiveOnes(int[] nums) {
        int max = 0; 
        int maxBreak = 0; 

        for( int i = 0 ; i < nums.Length; i++)
        {
            if(nums[i] == 1)
            {
                maxBreak = maxBreak + 1;
            }
            else if(nums[i] != 1) 
            {
                if(maxBreak >=  max)
                {
                   max =  maxBreak;    
                }
                maxBreak = 0; 
            }
        }

        if(maxBreak >  max)
        {
            max =  maxBreak;    
        }
        
        return max;
    }
}
```
## OpenAPI Code
```
public class Solution {
    public int FindMaxConsecutiveOnes(int[] nums) {
        int maxCount = 0;
        int currentCount = 0;

        foreach (int num in nums) {
            if (num == 1) {
                currentCount++;
                maxCount = Math.Max(maxCount, currentCount);
            } else {
                currentCount = 0;
            }
        }

        return maxCount;
    }
}

```
# Comparison

| Aspect               | Your Solution           | Clean Solution            | Notes                              |
| -------------------- | ----------------------- | ------------------------- | ---------------------------------- |
| **Correctness**      | ✔️ Correct              | ✔️ Correct                | Both are valid                     |
| **Time Complexity**  | **O(n)**                | **O(n)**                  | Equal                              |
| **Space Complexity** | **O(1)**                | **O(1)**                  | Equal                              |
| **Performance**      | Same                    | Same                      | Both do 1 pass                     |
| **Readability**      | Slightly more complex   | Cleaner & simpler         | Minor improvement                  |
| **Edge handling**    | Handled manually at end | Handled naturally in loop | Yours has an extra `if` after loop |
