# Top Data Structures and Algorithm Codes with Answers

1. ## [Check if Array Is Sorted and Rotated](https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/description/)

   
   Given an array nums, return true if the array was originally sorted in non-decreasing order, then rotated some number of positions (including zero). Otherwise, return false.  
   There may be duplicates in the original array.  
   Note: An array A rotated by x positions results in an array B of the same length such that A[i] == B[(i+x) % A.length], where % is the modulo operation.

   Example 1:  
   Input: nums = [3,4,5,1,2]  
   Output: true  
   Explanation: [1,2,3,4,5] is the original sorted array.  
   You can rotate the array by x = 3 positions to begin on the the element of value 3: [3,4,5,1,2].  

   Example 2:  
   Input: nums = [2,1,3,4]  
   Output: false  
   Explanation: There is no sorted array once rotated that can make nums.  

   Example 3:  
   Input: nums = [1,2,3]  
   Output: true  
   Explanation: [1,2,3] is the original sorted array.  
   You can rotate the array by x = 0 positions (i.e. no rotation) to make nums.

   Constraints:  
   1 <= nums.length <= 100  
   1 <= nums[i] <= 100

   ```
   class Solution {
   public:
    bool check(vector<int>& nums) {
        int count = 0;
        int n = nums.size();
        for (int i = 0; i < n; i++) {
            if (nums[i] > nums[(i + 1) % n]) {
                count++;
            }
           
            if (count > 1) {
                return false;
            }
        }

        return true;
    }
   };
   ```

2. ## [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)

   Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in nums.
    
   Consider the number of unique elements of nums to be k, to get accepted, you need to do the following things:  
   - Change the array nums such that the first k elements of nums contain the unique elements in the order they were present in nums initially. The remaining elements of nums are not important as well as the size of nums.  
   - Return k.

   Example 1:  
   Input: nums = [1,1,2]  
   Output: 2, nums = [1,2,_]  
   Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.  
   It does not matter what you leave beyond the returned k (hence they are underscores).  

   Example 2:  
   Input: nums = [0,0,1,1,1,2,2,3,3,4]  
   Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]  
   Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.  
   It does not matter what you leave beyond the returned k (hence they are underscores).

   Constraints:  
   1 <= nums.length <= 3 * 104  
   100 <= nums[i] <= 100  
   nums is sorted in non-decreasing order.

   ```
   class Solution {
   public:
    int removeDuplicates(vector<int>& nums) {
        int res = 0;
        for (int i = 0, j = 1; i < nums.size() && j < nums.size(); j++) {
            if (nums[i] != nums[j]) {
                nums[i + 1] = nums[j];
                i++;
                res = i;
            }
        }
        return res + 1;
    }
   };
   ```
