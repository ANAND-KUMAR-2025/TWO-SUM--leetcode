# Two Sum Problem

## Intuition
The goal is to find two numbers in an array that add up to a specified target. The naive approach would involve nested loops to check every pair, which would be inefficient for larger arrays. Instead, we can utilize a hash map (or dictionary) to store numbers and their indices as we iterate through the list. This allows us to quickly check if the complement (the number needed to reach the target) has already been encountered.

## Approach
1. Initialize an empty dictionary (`hash_map`) to store the numbers and their indices while iterating through the list.
2. For each number in the list:
   - Calculate its complement by subtracting the number from the target.
   - Check if the complement exists in `hash_map`:
     - If it does, return the index of the complement (found in `hash_map`) and the current index.
   - If it doesn't, store the current number and its index in `hash_map`.
3. This approach ensures that we only pass through the list once, making it efficient.

## Complexity
- **Time Complexity**: $$O(n)$$  
  We make a single pass through the array of size `n`, with each lookup and insertion operation in the hash map averaging $$O(1)$$.

- **Space Complexity**: $$O(n)$$  
  In the worst case, we may end up storing all `n` numbers in the hash map if no two numbers sum to the target. Thus, the space used is proportional to the number of elements in the list.

## Code
```python
from typing import List

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hash_map = {}
        for i, num in enumerate(nums):
            complement = target - num
            if complement in hash_map:
                return [hash_map[complement], i]
            hash_map[num] = i
