# LEETCODE-Array-1509
Sure, let's dry run the given code step by step to understand its execution and find the minimum difference after performing at most 3 changes.

```java
class Solution {
  public int minDifference(int[] nums) {
    final int n = nums.length;
    if (n < 5)
      return 0;

    int ans = Integer.MAX_VALUE;

    Arrays.sort(nums);

    // 1. Change nums[0..i) to nums[i].
    // 2. Change nums[n - 3 + i..n) to nums[n - 4 + i].
    for (int i = 0; i <= 3; ++i)
      ans = Math.min(ans, nums[n - 4 + i] - nums[i]);

    return ans;
  }
}
```

Let's take an example to dry run this code:

### Example
```java
int[] nums = {6, 6, 0, 1, 1, 4, 6};
```

#### Step-by-Step Execution:

1. **Initialization and Early Return Check:**
   - `final int n = nums.length;` sets `n` to 7.
   - Check if `n < 5`. Since 7 is not less than 5, we proceed.
   - Initialize `int ans = Integer.MAX_VALUE;`.

2. **Sorting the Array:**
   - Before sorting: `nums = {6, 6, 0, 1, 1, 4, 6}`
   - After sorting: `nums = {0, 1, 1, 4, 6, 6, 6}`

3. **Finding the Minimum Difference:**
   - Iterate with `i` from 0 to 3:
     - For `i = 0`: 
       - Calculate difference: `nums[n - 4 + 0] - nums[0] = nums[3] - nums[0] = 4 - 0 = 4`
       - Update `ans`: `ans = Math.min(Integer.MAX_VALUE, 4) = 4`
     - For `i = 1`: 
       - Calculate difference: `nums[n - 4 + 1] - nums[1] = nums[4] - nums[1] = 6 - 1 = 5`
       - Update `ans`: `ans = Math.min(4, 5) = 4`
     - For `i = 2`: 
       - Calculate difference: `nums[n - 4 + 2] - nums[2] = nums[5] - nums[2] = 6 - 1 = 5`
       - Update `ans`: `ans = Math.min(4, 5) = 4`
     - For `i = 3`: 
       - Calculate difference: `nums[n - 4 + 3] - nums[3] = nums[6] - nums[3] = 6 - 4 = 2`
       - Update `ans`: `ans = Math.min(4, 2) = 2`

4. **Return the Result:**
   - The final result `ans` is 2.

So, for the input array `{6, 6, 0, 1, 1, 4, 6}`, the minimum difference after performing at most 3 changes is 2.
