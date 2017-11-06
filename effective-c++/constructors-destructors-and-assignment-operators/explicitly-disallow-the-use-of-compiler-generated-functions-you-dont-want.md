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

If you don’t declare a copy constructor or a copy assignment operator, compilers may generate them for you. Your class thus supports copying. If, on the other hand, you do declare these functions, your class still supports copying. But the goal here is to _prevent_ copying！

The key to the solution is that all the compiler generated functions are public. To prevent these functions from being generated, you must declare them yourself, but there is nothing that requires that you declare them public. Instead, declare the copy constructor and the copy assignment operator _private_. By declaring a member function explicitly, you prevent compilers from generating their own version, and by making the function private, you keep people from calling it.

Member and friend functions can still call your private functions. Unless, that is, you are clever enough not to _define_ them. Then if somebody inadvertently calls one, they’ll get an error at link-time. **This trick — declaring member functions **_**private**_** and deliberately not implementing them — is so well established.**

Applying the trick to `HomeForSale` is easy:

```cpp
class HomeForSale{
public:
    ...
private:
    HomeForSale(const HomeForSale&); 
    HomeForSale& operator=(const HomeForSale&);  //declarations only     
};
```

With the above class definition, compilers will thwart client attempts to copy `HomeForSale` objects, and if you inadvertently try to do it in a member or a friend function, the linker will complain. It’s possible to move the link-time error up to compile time \(always a good thing — earlier error detection is better than later\) by declaring the copy constructor and copy assignment operator private not in `HomeForSale` itself, but in a base class specifically designed to prevent copying. The base class is simplicity itself:

```cpp
class Uncopyable{
protected:
    Uncopyable(){}                           //allow construction and 
    ~Uncopyable(){}                          // and destruction of derived objects
private:
    Uncopyable(const Uncopyable&);           // but prevent copying
    Uncopyable& operator=(const Uncopyable&);
};
```

To keep `HomeForSale` objects from being copied, all we have to do now is inherit from `Uncopyable`:

```cpp
class HomeForSale : private Uncopyable{  // class no longer
...                                      // defines copy ctor or 
};                                       // copy assign. operator
```



