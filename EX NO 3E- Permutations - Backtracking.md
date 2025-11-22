
# EX 3E Generate Permutations using Backtracking  Approach.
## AIM:
To write a Java program to for given constraints.
Given an array nums of distinct integers, return all the possible Permutation. You can return the answer in any order.
Example 1:
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
For example:
## Algorithm
1. Start and read the input array nums from the user.
2. Initialize an empty list ans to store all possible permutations.
3. Use a backtracking function that builds permutations by adding elements not yet used in the current list curr. 
4. When curr reaches the same length as nums, add a copy of it to ans, then backtrack by removing the last added element. 
5. Continue recursively exploring all possibilities until all permutations are generated, then print the final list of permutations and stop.  

## Program:
#### Developed by :ARCHANA T
#### Register Number:212223240013
```
import java.util.*;

public class Solution {

    public List<List<Integer>> permute(int[] nums) {
        //add your code here
        List<List<Integer>> ans=new ArrayList<>();
        backtrack(new ArrayList<>(),ans,nums);
        return ans;
    }

    public void backtrack(List<Integer> curr, List<List<Integer>> ans, int[] nums)
    {
        //Add your code here
        if(curr.size()==nums.length)
        {
            ans.add(new ArrayList<>(curr));
            return;
        }
        for(int num:nums)
        {
            if(!curr.contains(num))
            {
                curr.add(num);
                backtrack(curr,ans,nums);
                curr.remove(curr.size()-1);
            }
        }
    }    

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String inputLine = scanner.nextLine().trim();
        inputLine = inputLine.replaceAll(".*\\[|\\].*", ""); 
        String[] parts = inputLine.split(",");

        int[] nums = new int[parts.length];
        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }
        Solution solution = new Solution();
        List<List<Integer>> permutations = solution.permute(nums);
        System.out.println(permutations);
        scanner.close();
    }
}

```

## Output:
<img width="1060" height="154" alt="image" src="https://github.com/user-attachments/assets/74a323f1-c4b6-4e16-9893-531151102d0f" />



## Result:
The program successfully implemented and the expected output is verified.
