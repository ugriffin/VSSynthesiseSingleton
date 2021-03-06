# VSSynthesiseSingleton
www.urielgriffin.com / www.vetragames.com

Easy to use C++ singleton macro. Quickly and easily turn your class into a singleton with two lines of code, one in the class declaration and one in the implementation. 

# How to use:
Simply import <b>VSSynthesiseSingleton.h</b> into your class header, and call <b>VS_DECLARESINGLETON( _classname_, _accessorname_ );</b> where <b>_classname_</b> stands for the actual name of your class, and <b>_accessorname_</b> stands for the accessor name you wish to use for your singleton. Some example code:

<b>MySingleton.h</b>

```cpp
#include "VSSynthesiseSingleton.h"

class MySingleton
{
VS_DECLARESINGLETON(MySingleton,instance);

public:
int derp;

private:
int herp;
};
```

You also need to include some code in your class implementation.

Call <b>VS_SYNTHESISESINGLETON(__classname__,__accessorname__);</b> on your implementation file. Because of the way it's built, VSSynthesiseSingleton needs to hide your constructor and destructor from you. You therefore need to implement two functions which VSSynthesiseSingleton declares for you in case you would like to use a constructor or a destructor. The functions are <b>void _classname_::init()</b> and <b>void _classname_::destroy()</b>. These get respectively called the first time your singleton is initialised, and if it is destroyed. Example code:

<b>MySingleton.cpp

```cpp
#include "MySingleton.h"

VS_SYNTHESISESINGLETON(AnimationManager,instance);

//Your new constructor
void MySingleton::init()
{
//Code goes here.
}

//Your new destructor
void MySingleton::destroy()
{
//Code goes here.
}
```
