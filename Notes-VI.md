# Object Oriented Programing (Interview Prep) (Part-VI)

## 1. What is Encapsulation
- In normal terms Encapsulation is defined as wrapping up of data and information under a single unit. In Object Oriented Programming, Encapsulation is defined as binding together the data and the functions that manipulates them.

- Consider a real life example of encapsulation, in a company there are different sections like the accounts section, finance section, sales section etc. The finance section handles all the financial transactions and keep records of all the data related to finance. Similarly the sales section handles all the sales related activities and keep records of all the sales. Now there may arise a situation when for some reason an official from finance section needs all the data about sales in a particular month. In this case, he is not allowed to directly access the data of sales section. He will first have to contact some other officer in the sales section and then request him to give the particular data. 

- Encapsulation also lead to data abstraction or hiding.

- In C++ encapsulation can be implemented using Class and access modifiers. 

### Code:
```
#include<iostream>
#include<stdio.h>

using namespace std;

class company {

private: 

    int salesData = 500;

public:

    void salesDepManagerSet(int a) {

        salesData = a;
    }

    void salesDepManagerGet() {
        cout << salesData;
    }
};
int main() {    

    company E1;

    // E1.salesData = 1000; 
    /* Error occurs if an employee directly changes 
       sales departments data without manager permission*/

    E1.salesDepManagerSet(1000); // Correct method
    E1.salesDepManagerGet();
}
```

### Output:
```
1000
```

<strong>Note: Thus we can say that here, the variable x and the functions get() and set() are binded together which is nothing but encapsulation.</strong>

## 2. Need of Encapsulation
- For hiding the unnecessary data from user which are not belong to user ex:capsule is d beast example of encapsulation
because don't bother about what inside the capsule he want only become good 

## 3. How is encapsulation achieved
- As we have seen in above example, access specifiers plays an important role in implementing encapsulation in C++. The process of implementing encapsulation can be sub-divided into two steps:

- 1. The <strong>data members</strong> should be labeled as <strong>private</strong> using the private access specifiers.
- 2. The <strong>member function which manipulates the data members</strong> should be labeled as <strong>public</strong> using the public access specifier.


## 4. What is Abstraction?
- Abstraction means displaying only essential information and hiding the details. Data abstraction refers to providing only essential information about the data to the outside world, hiding the background details or implementation.

- Consider a real life example of a man driving a car. The man only knows that pressing the accelerators will increase the speed of car or applying brakes will stop the car but he does not know about how on pressing accelerator the speed is actually increasing, he does not know about the inner mechanism of the car or the implementation of accelerator, brakes etc in the car. This is what abstraction is.

## 5. How is Abstraction achived in c++?
- <strong>Using Access Specifiers:</strong>
### Code
```
#include <iostream>
using namespace std;

class implementAbstraction
{
	private:
		int a, b;

	public:
	
		// method to set values of
		// private members
		void set(int x, int y)
		{
			a = x;
			b = y;
		}
		
		void display()
		{
			cout<<"a = " <<a << endl;
			cout<<"b = " << b << endl;
		}
};

int main()
{
	implementAbstraction obj;
	obj.set(10, 20);
	obj.display();
	return 0;
}
```

### Output
```
a = 10
b = 20
```

- <strong>Using Header Files:</strong>
```
One more type of abstraction in C++ can be header files. For example, consider the pow() method present in math.h header file. Whenever we need to calculate power of a number, we simply call the function pow() present in the math.h header file and pass the numbers as arguments without knowing the underlying algorithm according to which the function is actually calculating power of numbers.
```

<strong>Advantages of Data Abstraction:</strong>

- Helps the user to avoid writing the low level code
- Avoids code duplication and increases reusability.
- Can change internal implementation of class independently without affecting the user.
- Helps to increase security of an application or program as only important details are provided to the user.


## 6. Encapsulation vs Abstraction
- Encapsulation is a way to achieve "information hiding" so, following your example, you don't "need to know the internal working of the mobile phone to operate" with it. You have an interface to use the device behaviour without knowing implementation details.

- Abstraction on the other side, can be explained as the capability to use the same interface for different objects. Different implementations of the same interface can exist. Details are hidden by encapsulation.

- <strong>You can do encapsulation without using abstraction, but if you wanna use some abstraction in your projects, you'll need encapsulation.</strong>
