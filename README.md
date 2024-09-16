# Subsets-II

Given an integer array nums that may contain duplicates, return all possible 
subsets
 (the power set).
The solution set must not contain duplicate subsets. Return the solution in any order.

Constraints:
1 <= nums.length <= 10
-10 <= nums[i] <= 10

class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        
        nums.sort()
        ans = [[]]
        memory = {i: 0 for i in set(nums)}
        
        for i in nums:
            l = len(ans)
            for s in ans[memory[i]:l]: ans.append(s+[i])
            memory[i] = l
        
        return ans
