* ## Polymorphic base classes should declare virtual destructors. If a class has any virtual functions, it should have a virtual destructor.
* ## Classes not designed to be base classes or not designed to be used polymorphically should not declare virtual destructors.

There are lots of ways to keep track of time, so it would be reasonable to create a `TimeKeeper` base class along with derived classes for different approaches to timekeeping:

```cpp
class TimeKeeper { 
public:
        TimeKeeper();
        ~TimeKeeper( );
        ...
};

class AtomicClock: public TimeKeeper { ... }; 
class WaterClock: public TimeKeeper { ... }; 
class WristWatch: public TimeKeeper { ... };
```

Many clients will want access to the time without worrying about the details of how it’s calculated, so a factory function— a function that returns a base class pointer to a newly-created derived class object — can be used to return a pointer to a timekeeping object:

```cpp
TimeKeeper* getTimeKeeper(); // returns a pointer to a 
                             // dynamically-allocated object 
                             // of a class derived from TimeKeeper
```

In keeping with the conventions of factory functions, the objects returned by `getTimeKeeper` are on the heap, so to avoid leaking memory and other resources, it’s important that each returned object be properly deleted:

```cpp
TimeKeeper* ptk = getTimeKeeper();  // get dynamically allocated object 
                                    // from TimeKeeper hierarchy
...                                 // use it
delete ptk;                         // release it to avoid resource leak
```

The problem is that `getTimeKeeper` returns a pointer to a derived class object \(e.g.,`AtomicClock`\), that object is being deleted via a base class pointer \(i.e., a `TimeKeeper*` pointer\), and the base class \(`TimeKeeper`\) has a _non-virtual_ destructor. This is a recipe for disaster, because C++ specifies that when a derived class object is deleted through a pointer to a base class with a non-virtual destructor, results are undefined. What typically happens at runtime is that the derived part of the object is never destroyed, thus leading to a curious “**partially destroyed**” object.

