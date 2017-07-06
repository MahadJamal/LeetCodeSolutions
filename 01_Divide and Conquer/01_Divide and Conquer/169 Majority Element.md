# 169 Majority Element

## Discription

Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.


## Solutions:

### Python

#### This problem can be solved in one line code in Python but following is divide and conquer implementation of this Problem: 
** (Please Note that Divide and Conquer is not the best choice for this problem) **
**__ This Solution will only work if their exist a majority element__**

```python
class Solution(object):
    
    Majority = {}
    
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        # if (len(nums)==0):
        #     return 0
        if (len(nums)==1):
            return nums[0]
        if (len(nums)==2):
            if(nums[0]==nums[1]):
                return nums[0]
#             else:
#                 elemL = self.majorityElement(nums[0])
#                 elemR = self.majorityElement(nums[1])
                
                
        k = len(nums)/2
        
        elemL = self.majorityElement(nums[:k])
        elemR = self.majorityElement(nums[k:])
        
        if ( elemL == elemR ):
            return elemL
        
        Lcount = self.GetFrequency( nums, elemL )
        Rcount = self.GetFrequency( nums, elemR )
        
        if Lcount > k:
            return elemL
        elif Rcount > k:
            return elemR

    
    def GetFrequency(self, nums, element):
        count = 0
        for i in nums:
            if(element == i):
                count += 1 
        return count
```

