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



