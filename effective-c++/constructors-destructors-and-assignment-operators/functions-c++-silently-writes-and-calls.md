If you don’t declare them yourself, compilers will declare their own versions of **a copy constructor**, **a copy assignment operator**, and **a destructor**. Furthermore, if you declare no constructors at all, compilers will also declare **a default constructor** for you. All these functions will be both _public_ and _inline._

If we write

```cpp
class Empty{};
```

It is essentially the same as 

```cpp
class Empty{
public:
    Empty(){...}                             // default constructor
    Empty(const Empty& rhs){...}             // copy constructor
    ~Emoty(){...}                            //destructor (see below 
                                             // for whether it's virtual or not)
    Empty& operator=(const Empty& rhs){...}  //copy-assignment operator
}; 
```

These functions are generated only if they are needed, but it doesn’t take much to need them. The following code will cause each function to be generated:

