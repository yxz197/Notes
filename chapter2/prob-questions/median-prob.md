## 3 random variables i.i.d from a uniform distribution 0 to 2, what is the probability that the median is greater than 1.5?

Google

$$$$

```r
count = 0
N = 1e7
for(i in 1:N){
  x = runif(3,0,2)
  if(median(x) > 1.5){
    count = count + 1
  }
}
```



