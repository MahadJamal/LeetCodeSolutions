#053 Maximum Subarray

## Discription

Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

For example, given the array [-2,1,-3,4,-1,2,1,-5,4],
the contiguous subarray [4,-1,2,1] has the largest sum = 6.



## Solutions:

### Python

#### This problem can be solved in one line code in Python but following is divide and conquer implementation of this Problem: 
** (Please Note that Divide and Conquer is not the best choice for this problem) **
**__ This Solution will only work if their exist a majority element__**

```python
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """

        (left_index, right_index, maxSum) = maximumSubArray(nums, 0, (len(nums) - 1 )) 
        print(left_index)
        print(right_index)
        print(maxSum)
        return maxSum
    
    
def maximumSubArray(nums, low, high):
    if ( low == high):
        return (low, high, nums[low])   #base case
    else:
        mid = (low + high)/2
        (left_low, left_high, left_sum) = maximumSubArray(nums, low, mid)
        (right_low, right_high, right_sum) = maximumSubArray(nums, mid+1, high)
        (cross_low, cross_high, cross_sum) = MAXCenterSum(nums, low, mid, high)

        if(left_sum >= right_sum and left_sum >= cross_sum):
            return (left_low,left_high, left_sum)
        elif (right_sum >= left_sum and right_sum >= cross_sum):
            return (right_low, right_high, right_sum)
        else:
            return (cross_low, cross_high, cross_sum)



def MAXCenterSum(nums, low , mid, high):
    left_sum = -99999
    Sum = 0
    max_left = 0
    max_right = 0
    for i in range(mid,low-1,-1):
        Sum = Sum + nums[i]
        if Sum > left_sum:
            left_sum = Sum
            max_left = i
    right_sum = -99999
    Sum = 0
    for j in range(mid+1,high+1):
        Sum = Sum + nums[j]
        if Sum > right_sum:
            right_sum = Sum
            max_right = j
    return (max_left, max_right, left_sum + right_sum)

```
