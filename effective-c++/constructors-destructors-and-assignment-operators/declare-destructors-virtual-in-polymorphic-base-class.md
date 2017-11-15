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



