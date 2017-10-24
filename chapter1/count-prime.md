## **204. Count Primes**

Count the number of prime numbers less than a non-negative number, $$n$$.



直接数肯定是要跪的，那该怎么办呢？

每次数到一个质数的时候，把它的倍数全部标记成不是质数。比如对一个质数 $$p$$ , 我们可以把$$2p, 3p, 4p,...$$全部标成不是质数。这里还可以优化一下，那就是不必从$$2p$$ 开始标记，因为它肯定在标记2的时候就被标了，所以可以直接从 $$$$$$p^2$$ 开始标。



```cpp
 int countPrimes(int n) {
        if (n<=2) return 0;
	vector<bool> checked(n, false);
	int sum = 1;
	int upper = sqrt(n);
	for (int i=3; i<n; i+=2) {
		if (!checked[i]) {
			sum++;
			//avoid overflow
			if (i>upper) continue;
			for (int j=i*i; j<n; j+=i) {
				checked[j] = true;
			}
		}
	}
	return sum;
      }
```



