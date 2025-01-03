# Top Data Structures and Algorithm Codes with Answers

## [Check if Array Is Sorted and Rotated](https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/description/)

Given an array `nums`, return true if the array was originally sorted in non-decreasing order, then rotated some number of positions (including zero). Otherwise, return false.

There may be duplicates in the original array.

Note: An array A rotated by x positions results in an array B of the same length such that A[i] == B[(i+x) % A.length], where % is the modulo operation.

### Example 1:
Input: nums = [3,4,5,1,2]  
Output: true  
Explanation: [1,2,3,4,5] is the original sorted array.  
You can rotate the array by x = 3 positions to begin on the element of value 3: [3,4,5,1,2].  

### Example 2:
Input: nums = [2,1,3,4]  
Output: false  
Explanation: There is no sorted array once rotated that can make nums.  

### Example 3:
Input: nums = [1,2,3]  
Output: true  
Explanation: [1,2,3] is the original sorted array.  
You can rotate the array by x = 0 positions (i.e. no rotation) to make nums.  

### Constraints:
- 1 <= nums.length <= 100
- 1 <= nums[i] <= 100

```cpp
class Solution {
public:
    bool check(vector<int>& nums) {
        int count = 0;
        int n = nums.size();

        for(int i=1; i<n; i++){
            if(nums[i-1] > nums[i]){
                count++;
            }
        }

        if(nums[n-1] > nums[0]){
            count++;
        }

        return count<=1;
    }
};
```
<br/>
<br/>

## [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)

Given an integer array `nums` sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in `nums`.

Consider the number of unique elements of `nums` to be `k`, to get accepted, you need to do the following things:
- Change the array `nums` such that the first `k` elements of `nums` contain the unique elements in the order they were present in `nums` initially. The remaining elements of `nums` are not important as well as the size of `nums`.
- Return `k`.

### Custom Judge:
The judge will test your solution with the following code:
```cpp
int[] nums = [...]; // Input array
int[] expectedNums = [...]; // The expected answer with correct length

int k = removeDuplicates(nums); // Calls your implementation

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
```
<br/>
<br/>

## [Rotate Array](https://leetcode.com/problems/rotate-array/description/)

Given an integer array `nums`, rotate the array to the right by `k` steps, where `k` is non-negative.

### Example 1:
Input: nums = [1,2,3,4,5,6,7], k = 3  
Output: [5,6,7,1,2,3,4]  
Explanation:  
rotate 1 step to the right: [7,1,2,3,4,5,6]  
rotate 2 steps to the right: [6,7,1,2,3,4,5]  
rotate 3 steps to the right: [5,6,7,1,2,3,4]  

### Example 2:
Input: nums = [-1,-100,3,99], k = 2  
Output: [3,99,-1,-100]  
Explanation:  
rotate 1 step to the right: [99,-1,-100,3]  
rotate 2 steps to the right: [3,99,-1,-100]  

### Constraints:
- 1 <= nums.length <= 10^5
- -2^31 <= nums[i] <= 2^31 - 1
- 0 <= k <= 10^5

```cpp
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        int n = nums.size();
        k = k % n;
        reverse(nums.begin(), nums.end());
        reverse(nums.begin(), nums.begin() + k);
        reverse(nums.begin() + k, nums.end());
    }
};
