## Two Pointers

### 167. Two Sum II - Input Array Is Sorted
* Given a 1-indexed array of integers numbers that is already sorted in non-decreasing order, find two numbers such that they add up to a specific target number. Let these two numbers be numbers[index1] and numbers[index2] where 1 <= index1 < index2 <= numbers.length.

* Return the indices of the two numbers, index1 and index2, added by one as an integer array [index1, index2] of length 2.

* The tests are generated such that there is exactly one solution. You may not use the same element twice.Your solution must use only constant extra space.

```
Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].
```

```
public class Solution {

    public int[] twoSum(int[] nums, int target) {
     int left=0;
     int right=nums.length-1;
     while(left < right){
        int sum=nums[left] + nums[right];
        if(sum == target){
            return new int[]{left+1, right+1};
        }
        else if(sum < target){
            left++;
        }
        else{
            right--;
        }
     }
     return new int[]{};
    }
}
```

### 11. Container With Most Water
* You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

* Find two lines that together with the x-axis form a container, such that the container contains the most water.

* Return the maximum amount of water a container can store.

* Notice that you may not slant the container.
```
class Solution {
    public int maxArea(int[] height) {
        int left=0;
        int right=height.length-1;
        int maxArea=0;
        while(left < right) {
            int currArea = Math.min(height[left], height[right]) * (right-left);
            maxArea=Math.max(currArea, maxArea);
            if(height[left] < height[right]){
                left++;
            }
            else {
                right--;
            }
        }
        return maxArea;
    }
}

"""
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
"""
```
