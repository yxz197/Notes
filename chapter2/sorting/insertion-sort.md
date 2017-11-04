## Insertion Sort

顾名思义，就是把元素一个个地往前面排好序的数组里面插入。

几个注意事项：

1. 容易推出insertion sort的复杂度是$$O(n^2)$$，不过那是默认 compare 和 swap 的cost相差无几。如果compare的cost明显高于swap，那么复杂度可以降低到$$O(n\log n)$$。为什么呢？因为比较的时候可以用binary search。
2. Insertion sort, 相比于merge sort的，一个优点是，它是in place的。

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



