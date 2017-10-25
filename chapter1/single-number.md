## 136. Single Number

Given an array of integers, every element appears twice except for one. Find that single one.

思路：异或运算 XOR，注意到 a XOR a = 0，XOR又是可交换的运算符，答案就很简单啦

```cpp
    int singleNumber(vector<int>& nums) {
        int res = 0;
        for(auto num : nums){
            res ^= num;
        }
        return res;

//         map<int, int> imap;
//         for(auto i : nums){
//             imap[i]++;
//         }
//         for(auto i : nums){
//             if(imap[i] == 1){
//                 return i;
//             }
//         }
    }
```

## 260. Single Number III

Given an array of numbers`nums`, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.

思路：用xor跑两遍。第一遍，得到a和b的xor值。注意，这个值至少有一个set bit，就是说至少有一位上是1，取出这个最右边的一个1，比如index是k。第二遍，把数组里面的元素分成两个集合，在k上是1的放入集A，在k上是0的放入集合B, 那么a和b一定会在不同的集合，比如a在A, b在B。对这两个集合再做一次全体xor运算，分别得到a和b。

```cpp
  vector<int> singleNumber(vector<int>& nums) {
        // Pass 1 : 
        // Get the XOR of the two numbers we need to find
        int diff = accumulate(nums.begin(), nums.end(), 0, bit_xor<int>());
        // Get its last set bit
        diff &= -diff;

        // Pass 2 :
        vector<int> res = {0, 0}; // this vector stores the two numbers we will return
        for (int num : nums)
        {
            if ((num & diff) == 0) // the bit is not set
            {
                res[0] ^= num;
            }
            else // the bit is set
            {
                res[1] ^= num;
            }
        }
        return res;
        // map<int, int> res;
        // vector<int> r;
        // for(auto num:nums){
        //     res[num]++;
        // }
        // for(auto i : res){
        //     if(i.second == 1){
        //         r.push_back(i.first);
        //     }
        // }
        // return r;
    }
```



