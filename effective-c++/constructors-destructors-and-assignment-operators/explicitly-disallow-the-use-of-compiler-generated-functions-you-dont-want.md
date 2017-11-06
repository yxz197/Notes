## To disallow functionality automatically provided by compilers, declare the corresponding member functions `private` and give no implementations. Using a base class like `Uncopyable` is one way to do this.

Real estate agents sell houses, and a software system supporting such agents would naturally have a class representing homes for sale:

```cpp
class HomeForSale{...};
```

As every real estate agent will be quick to point out, every property is unique — no two are exactly alike. That being the case, the idea of making a _copy_ of a `HomeForSale` object makes little sense. You’d thus like attempts to copy `HomeForSale` objects to not compile:

```cpp
HomeForSale h1;
HomeForSale h2;

HomeForSale h3(h1); // attempt to copy h1, should
                    // not compile
h1 = h2;            // attempt to copy h2, should
                    // not compile
```



