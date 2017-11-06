# Design a class to calculate moving average.

[Leetcode Link](https://leetcode.com/problems/moving-average-from-data-stream/description/)

```cpp
class MovingAverage{
private:
    double sum;
    queue<int> que;
    int aveSize;
public:
    MovingAverage(int size): aveSize(size), sum(0){}
    double next(int val){
        sum += val;
        que.push(val);
        int queueSize = int(que.size());
        if(queueSize <= aveSize){
            return sum/queueSize;
        } else{
            sum -= que.front();
            que.pop();
            return sum/aveSize;
        }
    }
};
```

[Check here for moving variance. ](https://www.johndcook.com/blog/standard_deviation/)

