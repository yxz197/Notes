## 496. Next Greater Element I

You are given two arrays **\(without duplicates\)**`nums1`and`nums2`where`nums1`’s elements are **subset** of`nums2`. Find all the next greater numbers for`nums1`'s elements in the corresponding places of`nums2`.

The Next Greater Number of a number **x **in`nums1`is the first greater number to its right in`nums2`. If it does not exist, output -1 for this number.

思路：如果有一串递减数列 3，2，1，然后突然来了一个6，那么6是3，2，1的next greater element。怎么记忆和记录这个性质呢？

建一个stack，对 `nums2` 中的元素，记录单调递减的子列，如果下一个`num2`中的元素，x，比stack的top大，那就不停pop，pop出来的元素的next element都是 x.

```cpp
  vector<int> nextGreaterElement(vector<int>& findNums, vector<int>& nums) {
        vector<int> result;
        stack<int> s;
        unordered_map<int, int> m;
        for(int i = 0; i < nums.size(); ++i){
                while(!s.empty() && s.top() < nums[i]){
                    m[s.top()] = nums[i];
                    s.pop();
                }
            s.push(nums[i]);
        }
        for(auto i : findNums){
            if(m.find(i) != m.end()){
                result.push_back(m[i]);
            }else{
                result.push_back(-1);
            }
        }
        return result;
    }
```



