
# EX 3C Tug of War problem - Backtracking.
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm
1. Start and read the array size n and its elements into nums[].
2. Calculate the total sum of all elements; if it’s odd, return false since equal partition isn’t possible.
3. Set the target sum as half of the total sum and initialize a boolean array dp[] where dp[i] indicates if a sum i can be formed.
4. For each number, update dp[j] (from target down to num) as true if dp[j] or dp[j - num] is true, building up all possible subset sums. 
5. Finally, check dp[target] — if true, equal partition exists; print the result and stop.  

## Program:
#### Developed by:ARCHANA T
#### Register Number :212223240013
```
import java.util.Scanner;

public class Solution {

    public boolean canPartition(int[] nums) {
        int totalSum = 0;
        for (int num : nums) {
            totalSum += num;
        }

        // If total sum is odd, it can't be partitioned equally
        if (totalSum % 2 != 0) {
            return false;
        }

        int target = totalSum / 2;
        boolean[] dp = new boolean[target + 1];
        dp[0] = true; // base case: sum 0 is always possible

        // For each number in nums, update dp array
        for (int num : nums) {
            for (int j = target; j >= num; j--) {
                dp[j] = dp[j] || dp[j - num];
            }
        }

        return dp[target];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();

        int n = scanner.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }

        boolean canBePartitioned = sol.canPartition(nums);
        System.out.println(canBePartitioned);
        scanner.close();
    }
}

```

## Output:

<img width="354" height="173" alt="image" src="https://github.com/user-attachments/assets/55565b44-a24d-4471-bf03-c18912df76b2" />


## Result:
The program successfully implemented and the expected output is verified.
