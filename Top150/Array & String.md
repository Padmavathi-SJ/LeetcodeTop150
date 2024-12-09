## Arrays & Strings

### 135. Candy
* There are n children standing in a line. Each child is assigned a rating value given in the integer array ratings.You are giving candies to these children subjected to the following requirements:
* Each child must have at least one candy.
* Children with a higher rating get more candies than their neighbors.
* Return the minimum number of candies you need to have to distribute the candies to the children.

```
Example 1:

Input: ratings = [1,0,2]
Output: 5
Explanation: You can allocate to the first, second and third child with 2, 1, 2 candies respectively.
```
### code using java
```
class Solution {
    public int candy(int[] ratings) {
        int n= ratings.length;
        int[] candies=new int[n];
        Arrays.fill(candies, 1);
        for(int i=1; i<n; i++){
            if(ratings[i] > ratings[i-1]){
                candies[i] = candies[i-1]+1;
            }
        }
        for(int i=n-2; i>=0; i--){
            if(ratings[i] > ratings[i+1]){
                candies[i]=Math.max(candies[i], candies[i+1]+1);
            }
        }
        int totalCandies=0;
        for(int candy:candies){
            totalCandies+=candy;
        }
        return totalCandies;
    }
}
```

### 42. Trapping Rain Water
* Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

```
Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.
```

* code using java
```
class Solution {
    public int trap(int[] height){
       int len=height.length;
       int[] left=new int[len];
       left[0]=height[0];
       int[] right=new int[len];
       right[len-1]=height[len-1];
       for(int i=1; i<len; i++){
        left[i]=Math.max(height[i], left[i-1]);
       }
       for(int i=len-2; i>=0; i--){
        right[i]=Math.max(height[i], right[i+1]);
       }
       int water=0;
       for(int i=0; i<len; i++){
        water += Math.min(left[i], right[i]) - height[i];
       }
       return water;
    }
}
```
