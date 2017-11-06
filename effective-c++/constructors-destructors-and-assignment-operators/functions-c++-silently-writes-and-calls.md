## 

## **Compliers may implicitly generate a class's default constructor, copy constructor, copy assignment operator, and destructor.**

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
    ~Empty(){...}                            //destructor (see below 
                                             // for whether it's virtual or not)
    Empty& operator=(const Empty& rhs){...}  //copy-assignment operator
};
```

These functions are generated only if they are needed, but it doesn’t take much to need them. The following code will cause each function to be generated:

```cpp
Empty e1;     \\default constructor
              \\destructor
Empty e2(e1); \\copy constructor
e2 = e1;      \\copy assignment operator
```

Note that the generated destructor is non-virtual unless it’s for a class inheriting from a base class that itself declares a virtual destructor \(in which case the function’s virtualness comes from the base class\).

As for the copy constructor and the copy assignment operator, the compiler-generated versions simply copy each non-static data member of the source object over to the target object. For example, consider a `NamedObject` template that allows you to associate names with objects of type T:

```cpp
template<typename T>
class NamedObject{
public:
    NamedObject(const char* name, const T& value);
    NamedObject(const std::string& name, const T& value);
    ...
private:
    std::string nameValue;
    T objectValue;
};
```

Because a constructor is declared in `NamedObject`, compilers won’t generate a default constructor. This is important. It means that if you’ve carefully engineered a class to require constructor arguments, you don’t have to worry about compilers overriding your decision by blithely adding a constructor that takes no arguments.

`NamedObject` declares neither copy constructor nor copy assignment operator, so compilers will generate those functions \(if they are needed\). Look, then, at this use of the copy constructor:

```cpp
NamedObject<int> no1("SPN", 2);
NamedObject<int> no2(no1); //calls copy constructor
```

but in general, compiler-generated copy assignment operators behave as I’ve described **only when the resulting code is both legal and has a reasonable chance of making sense**. If either of these tests fails, compilers will refuse to generate an `operator=` for your class.

For example, suppose `NamedObject` were defined like this, where `nameValue` is a _reference_ to a string and `objectValue` is a `const T`:

```cpp
template<typename T>
class NamedObject{
public:
    // this ctor no longer takes a const name, because nameValue
    // is now a reference-to-non-const string. The char* constructor 
    // is gone, because we must have a string to refer to.
    NamedObject(std::string& name, const T& value);
    ...                              //as above, assume no
                                     //operator= is declared
private:
   std::string& nameValue;           //this is now a reference
   const T objectValue;              //this is now const
}
```

Now consider what should happen here?

```cpp
std::string s1("new");
std::string s2("old");

NamedObject<int> p(s1,2);
NamedObject<int> s(s2,3);

p = s; // what should happen here?
```

After the assignment, should `p.nameValue` refer to the `string` referred to by `s.nameValue`, i.e., should the reference itself be modified? No, because C++ does not provide a way to make a reference refer to a different object.

Alternatively, should the `string` object to which `p.nameValue` refers be modified, thus affecting other objects that hold pointers or references to that `string`, i.e., objects not directly involved in the assignment? No.

In fact, it will not compile.

* If you want to support copy assignment in a class containing a reference member, you must define the copy assignment operator yourself.

* Similarly for classes containing `const` members.

* Compilers reject implicit copy assignment operators in derived classes that inherit from base classes declaring the copy assignment operator `private`.



