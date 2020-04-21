
#### 寻找旋转排序数组中的最小值 II
- 以下是对剑指Offer（六）的一种情况进行讨论：即当数组中存在重复元素时

##### C++实现
```cpp
class Solution {
public:
    int findMin(vector<int>& nums) {
        int left = 0;
        int right = nums.size() - 1;
        int mid = 0;
        while(!nums.empty() && left<right){
            if(nums[left]<nums[right]){
                return nums[left];
            }
            mid = left + (right - left)/2;
            if(nums[left] == nums[mid] && nums[left] == nums[right]){
                int result = nums[left];
                for(int i = left + 1;i<right;i++){
                    if(nums[i]<result){
                        result = nums[i];
                    }
                }
                return result;
            }
            if(nums[left]<nums[mid]){
                left = mid + 1;
            }
            else if(nums[mid]<nums[right]){
                right = mid;
            }
            else{
                left = left + 1;
            }
        }
        return nums[left];

    }
};
```

##### Python实现

```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        left = 0
        right = len(nums) - 1
        while left < right:
            if nums[left]<nums[right]:
                return nums[left]
            mid = left + (right - left)//2
            if nums[left] == nums[mid] and nums[right] == nums[mid]:
                result = nums[left]
                for i in range(left+1,right):
                    if nums[i]<result:
                        result = nums[i]
                return result
            if nums[left]<nums[mid]:
                left = mid + 1
            elif nums[mid]<nums[right]:
                right = mid
            else:
                left = left + 1
            
        return nums[left]
```
