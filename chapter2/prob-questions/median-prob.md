## 3 random variables i.i.d from a uniform distribution 0 to 2, what is the probability that the median is greater than 1.5?

Google

$$\quad P(X_{(2)} > 1.5) \\ = P(X_{(1)} > 1.5) + P(X_{(1)}\le 1.5 < X_{(2)}\le X_{(3)})\\ = (1/4)^3 + \left(\frac{3}{4}\frac{1}{4}\frac{1}{4}\right)\times 3\\=5/32$$

```py
count = 0
N = 1e7
for(i in 1:N){
  x = runif(3,0,2)
  if(median(x) > 1.5){
    count = count + 1
  }
}
```

