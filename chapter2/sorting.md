## 1.Insertion Sort

顾名思义，就是把元素一个个地往前面排好序的数组里面插入。

```cpp
void insertionSort(vector<int>& nums){
    int n = int(nums.size());
    for (int i = 1; i < n; ++i)
    {
        int key = nums[i];
        int j = i-1;
        
        /* Move elements of nums[0..i-1], that are
         greater than key, to one position ahead
         of their current position */
        while (j >= 0 && nums[j] > key)
        {
            nums[j+1] = nums[j];
            j--;
        }
        nums[j+1] = key;
    }
}
```



