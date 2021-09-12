# Object Oriented Programing (Interview Prep) (Part-III)

## 1. Virtual Function in C++
- A virtual function is a member function which is declared within a base class and is re-defined(Overriden) by a derived class. When you refer to a derived class object using a pointer or a reference to the base class, you can call a virtual function for that object and execute the derived class’s version of the function. 
- i.e <strong>Let's say we two function with same name but different functionality. One of them is in parent class and other in the derived class(child class). Now the compiler takes help of virtual function to distinguish between these two functions.</strong>
- Virtual functions ensure that the correct function is called for an object, regardless of the type of reference (or pointer) used for function call.
- They are mainly used to achieve Runtime polymorphism.
- <strong>Functions are declared with a virtual keyword in base class.</strong>
- The resolving of function call is done at Run-time.

### Rules for virtual function
<ol>
  <li>Virtual functions cannot be static.</li>
  <li>A virtual function can be a friend function of another class.</li>
  <li>Virtual functions should be accessed using pointer or reference of base class type to achieve run time polymorphism.</li>
  <li>The prototype of virtual functions should be the same in the base as well as derived class.</li>
  <li>They are always defined in the base class and overridden in a derived class. It is not mandatory for the derived class to override (or re-define the virtual function), in that case, the base class version of the function is used.</li>
  <li>A class may have virtual destructor but it cannot have a virtual constructor.</li>
</ol>


### Compile-time(early binding) VS run-time(late binding) behavior of Virtual Functions

### Code
```
// CPP program to illustrate
// concept of Virtual Functions

#include <iostream>
using namespace std;

class base {
public:
	virtual void print()
	{
		cout << "print base class" << endl;
	}

	void show()
	{
		cout << "show base class" << endl;
	}
};

class derived : public base {
public:
	void print()
	{
		cout << "print derived class" << endl;
	}

	void show()
	{
		cout << "show derived class" << endl;
	}
};

int main()
{
	base* bptr;
	derived d;
	bptr = &d;

	// virtual function, binded at runtime
	bptr->print();

	// Non-virtual function, binded at compile time
	bptr->show();
}
```

### Output

```
print derived class
show base class
```

### Explanation: 
- Runtime polymorphism is achieved only through a pointer (or reference) of base class type. Also, a base class pointer can point to the objects of base class as well as to the objects of derived class. In above code, base class pointer ‘bptr’ contains the address of object ‘d’ of derived class.
- Late binding(Runtime) is done in accordance with the content of pointer (i.e. location pointed to by pointer) and Early binding(Compile time) is done according to the type of pointer, since print() function is declared with virtual keyword so it will be bound at run-time (output is print derived class as pointer is pointing to object of derived class ) and show() is non-virtual so it will be bound during compile time(output is show base class as pointer is of base type ).

## 2. Abstract class and pure virtual function in C++
- Sometimes implementation of all function cannot be provided in a base class because we don’t know the implementation. Such a class is called abstract class.
- <strong>For example, let Shape be a base class. We cannot provide implementation of function draw() in Shape, but we know every derived class must have implementation of draw(). Similarly an Animal class doesn’t have implementation of move() (assuming that all animals move), but all animals must know how to move.</strong>
- We cannot create objects of abstract classes.
- <strong>An abstract class must have a pure virtual function. There can multiple Pure virtual functions.</strong>

### Code
```
#include <bits/stdc++.h>

using namespace std;


// Abstract class (A class which is made to derive other classes)
class shape2D {

protected:
// Setting this variables as protected, so that only the derived (child) class can use them.
    int height;
    int width;

public:

    virtual int area() = 0; // defining pure virtual function. Since formula for different shapes is different.

    void setwidth(int w) {

        width = w;
    }

    void setheight(int h) {

        height = h;
    }
};


class rectangle: public shape2D {

public:
    int area() {

        return (width*height);
    }
};

class triangle: public shape2D {

public:
    int area() {

        return (0.5*width*height);
    }
};


int main() {

    rectangle R;

    R.setwidth(10);
    R.setheight(10);

    cout << R.area() << endl;


    triangle T;

    T.setheight(10);
    T.setwidth(10);

    cout << T.area() << endl;
    return 0;
}
```

### Output

```
100
50
```

## 3. Final specifier in c++
- In Java, we can use final for a function to make sure that it cannot be overridden. We can also use final in Java to make sure that a class cannot be inherited. Similarly, the latest C++ standard C++ 11 added final. 
- <strong>Use of final specifier in C++ 11:</strong>
- Sometimes you don’t want to allow derived class to override the base class’ virtual function. C++ 11 allows built-in facility to prevent overriding of virtual function using final specifier. 

### Code

```
#include <iostream>
using namespace std;

class Base
{
public:
	virtual void myfun() final
	{
		cout << "myfun() in Base";
	}
};
class Derived : public Base
{
	void myfun()
	{
		cout << "myfun() in Derived\n";
	}
};

int main()
{
	Derived d;
	Base &b = d;
	b.myfun();
	return 0;
}
```

### Output

```
prog.cpp:14:10: error: virtual function ‘virtual void Derived::myfun()’
     void myfun()
          ^
prog.cpp:7:18: error: overriding final function ‘virtual void Base::myfun()’
     virtual void myfun() final 
```

- 2nd use of final specifier: 
final specifier in C++ 11 can also be used to prevent inheritance of class / struct. If a class or struct is marked as final then it becomes non inheritable and it cannot be used as base class/struct. 

### Code

```
#include <iostream>
class Base final
{
};

class Derived : public Base
{
};

int main()
{
	Derived d;
	return 0;
}
```

### Output

```
error: cannot derive from ‘final’ base ‘Base’ in derived type ‘Derived’
 class Derived : public Base
```

- Unlike Java, final is not a keyword in C++ 11. final has meaning only when used in above contexts, otherwise it’s just an identifier. 
One possible reason to not make final a keyword is to ensure backward compatibility. There may exist production codes which use final for other purposes.

### Code

```
#include <iostream>
using namespace std;

int main()
{
	int final = 20;
	cout << final;
	return 0;
}
```

### Output

```
20
```

## 4. this keyword in c++
#### In C++ programming, this is a keyword that refers to the current instance of the class. There can be 3 main usage of this keyword in C++.
- It can be used to pass current object as a parameter to another method.
- It can be used to refer current class instance variable.
- It can be used to declare indexers.

### Code

```
#include <iostream>  
using namespace std;  
class Employee {  
   public:  
       int id; //data member (also instance variable)      
       string name; //data member(also instance variable)  
       float salary;  
       Employee(int id, string name, float salary)    
        {    
            this->id = id;    
            this->name = name;    
            this->salary = salary;   
        }    
       void display()    
        {    
            cout<<id<<"  "<<name<<"  "<<salary<<endl;    
        }    
};  
int main(void) {  
    Employee e1 =Employee(101, "Sonoo", 890000); //creating an object of Employee   
    Employee e2=Employee(102, "Nakul", 59000); //creating an object of Employee  
    e1.display();    
    e2.display();    
    return 0;  
}
```

### Output

```
101  Sonoo  890000
102  Nakul  59000
```


## 5. New operator in c++
### Memory allocation on stack.


### Code
```
#include<iostream>

using namespace std;

class car
{
    string name;
    int num;

    public:
        car(string a, int n)
        {
            cout << "Constructor called" << endl;
            this ->name = a;
            this ->num = n;
        }

        void enter()
        {
            cin>>name;
            cin>>num;
        }

        void display()
        {
            cout << "Name: " << name << endl;
            cout << "Num: " << num << endl;
        }
};

int main()
{
    // Allocating memory on stack
    car c1("Honda", 2017);

    c1.display();

    return 0;
}
```

### Output
```
Constructor called
Name: Honda
Num: 2017
```

- <strong>When to allocate memory on stack</strong>
- Perfomance becomes faster.
- This program got executed in 623ms.

- <strong>When not to allocate memory on stack</strong>
- If we want to allocate object of big size.
- Also if we want scope of object outside a function too. i.e we should decide when we have to erase object from the memory.


### Memory allocation on Heap or using new operator.
- The new operator is an operator which denotes a request for memory allocation on the Heap. If sufficient memory is available, new operator initializes the memory and returns the address of the newly allocated and initialized memory to the pointer variable. When you create an object of class using new keyword(normal new).

### Code
```
// CPP program to illustrate
// use of new keyword
#include<iostream>
using namespace std;
class car
{
	string name;
	int num;

	public:
		car(string a, int n)
		{
			cout << "Constructor called" << endl;
			this ->name = a;
			this ->num = n;
		}

		void enter()
		{
			cin>>name;
			cin>>num;
		}

		void display()
		{
			cout << "Name: " << name << endl;
			cout << "Num: " << num << endl;
		}
};

int main()
{
	// Using new keyword
	car *p = new car("Honda", 2017);
	p->display();
	
	delete p;
}
```

### Output
```
Constructor called
Name: Honda
Num: 2017
```

- We need not use new everywhere in c++.
- Only when we need to allocate big size object on heap.
- Or we require scope of particular object to be outside some function too.
- <strong>Note we need to deallocate memory in this case.</strong>


## 6. Const keyword in C++
- If we make a varialble as <strong>const</strong> then we can initialize that variable only once.
- Also there two ways to initialize a <strong>const</strong> variable.

```
const int var = 5;
```

```
const int* var = &x;

x = 10;
```
