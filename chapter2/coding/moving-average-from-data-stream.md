# Design a class to calculate moving average.

[https://leetcode.com/problems/moving-average-from-data-stream/description/](https://leetcode.com/problems/moving-average-from-data-stream/description/ "Leetcode Link")

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



