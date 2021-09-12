# Object Oriented Programing (Interview Prep) (Part-IV)

## 1. What is Polymorphism
- The word polymorphism means having many forms. In simple words, we can define polymorphism as the ability of a message to be displayed in more than one form. 
- A real-life example of polymorphism, a person at the same time can have different characteristics. Like a man at the same time is a father, a husband, an employee. So the same person posses different behavior in different situations. This is called polymorphism. 
- Polymorphism is considered as one of the important features of Object Oriented Programming.
 
- <strong>In C++ polymorphism is mainly divided into two types:</strong>
- Compile time Polymorphism
- Runtime Polymorphism

![polymorphism-image](https://media.geeksforgeeks.org/wp-content/uploads/20200703160531/Polymorphism-in-CPP.png)

## 2. Function Overloading in C++
- Function overloading is a feature of object oriented programming where two or more functions can have the same name but different parameters.

### Code
```
#include <iostream>
using namespace std;

void print(int i) {
cout << " Here is int " << i << endl;
}
void print(double f) {
cout << " Here is float " << f << endl;
}
void print(char const *c) {
cout << " Here is char* " << c << endl;
}

int main() {
print(10);
print(10.10);
print("ten");
return 0;
}
```

### Output
```
Here is int 10 
Here is float 10.1 
Here is char* ten
```

## 3.Functions that cannot be overloaded in C++
- Function declarations that differ only in the return type. For example, the following program fails in compilation.
```
#include<iostream>
int foo() {
return 10;
}

char foo() {
return 'a';
}

int main()
{
char x = foo();
getchar();
return 0;
}
```
- Member function declarations with the same name and the name parameter-type-list cannot be overloaded if any of them is a static member function declaration. For example, following program fails in compilation.
```
#include<iostream>
class Test {
static void fun(int i) {}
void fun(int i) {}
};

int main()
{
Test t;
getchar();
return 0;
}
```

- Parameter declarations that differ only in the presence or absence of const and/or volatile are equivalent. That is, the const and volatile type-specifiers for each parameter type are ignored when determining which function is being declared, defined, or called. For example, following program fails in compilation with error “redefinition of `int f(int)’ “
```
#include<iostream>
#include<stdio.h>

using namespace std;

int f ( int x) {
	return x+10;
}

int f ( const int x) {
	return x+10;
}

int main() {	
getchar();
return 0;
}
```

## 4.Operator Overloading in C++
- In C++, we can make operators to work for user defined classes. This means C++ has the ability to provide the operators with a special meaning for a data type, this ability is known as operator overloading.
- For example, we can overload an operator ‘+’ in a class like String so that we can concatenate two strings by just using +.


### Code
```
#include<iostream>
using namespace std;

class Complex {
private:
	int real, imag;
public:
	Complex(int r = 0, int i =0) {real = r; imag = i;}
	
	// This is automatically called when '+' is used with
	// between two Complex objects
	Complex operator + (Complex const &obj) {
		Complex res;
		res.real = real + obj.real;
		res.imag = imag + obj.imag;
		return res;
	}
	void print() { cout << real << " + i" << imag << endl; }
};

int main()
{
	Complex c1(10, 5), c2(2, 4);
	Complex c3 = c1 + c2; // An example call to "operator+"
	c3.print();
}
```

### Output
```
12 + i9
```

- Can we overload all operators?
- Almost all operators can be overloaded except few. Following is the list of operators that cannot be overloaded.
```
. (dot) 
:: 
?: 
sizeof 
```

## 5.C++ Function Overriding?
- As we know, inheritance is a feature of OOP that allows us to create derived classes from a base class. The derived classes inherit features of the base class.
- Suppose, the same function is defined in both the derived class and the based class. Now if we call this function using the object of the derived class, the function of the derived class is executed.
- This is known as function overriding in C++. The function in derived class overrides the function in base class.

### Code 
```
// C++ program to demonstrate function overriding

#include <iostream>
using namespace std;

class Base {
   public:
    void print() {
        cout << "Base Function" << endl;
    }
};

class Derived : public Base {
   public:
    void print() {
        cout << "Derived Function" << endl;
    }
};

int main() {
    Derived derived1;
    derived1.print();
    return 0;
}
```

### Output
```
Derived Function
```
