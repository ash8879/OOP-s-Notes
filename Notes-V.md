# Object Oriented Programing (Interview Prep) (Part-V)

## 1. What is Inheritance
- The capability of a class to derive properties and characteristics from another class is called Inheritance. Inheritance is one of the most important feature of Object Oriented Programming. 
- <strong>Sub Class:</strong>   The class that inherits properties from another class is called Sub class or Derived Class. 
- <strong>Super Class:</strong> The class whose properties are inherited by sub class is called Base Class or Super class. 
- <strong>Inheritance represents the IS-A relationship.</strong>

## 2. Why and when to use inheritance?
- Consider a group of vehicles. You need to create classes for Bus, Car and Truck. 
- The methods fuelAmount(), capacity(), applyBrakes() will be same for all of the three classes. 
- If we create these classes avoiding inheritance then we have to write all of these functions in each of the three classes as shown in below figure: 

![GfG Image](https://media.geeksforgeeks.org/wp-content/uploads/inheritance.png)

- We can clearly see that above process results in duplication of same code 3 times. This increases the chances of error and data redundancy.
- To avoid this -> You can clearly see that above process results in duplication of same code 3 times. This increases the chances of error and data redundancy.

![](https://media.geeksforgeeks.org/wp-content/uploads/inheritance2.png)

## 3. Implementing inheritance in C++: 
- For creating a sub-class which is inherited from the base class we have to follow the below syntax. 

```
class subclass_name : access_mode base_class_name
{
  //body of subclass
};
```

## 4. Access Mode
<strong>Modes of Inheritance</strong>
- <strong>Public mode:</strong> If we derive a sub class from a public base class. Then the public member of the base class will become public in the derived class and protected members of the base class will become protected in derived class.

- <strong>Protected mode:</strong> If we derive a sub class from a Protected base class. Then both public member and protected members of the base class will become protected in derived class.

- <strong>Private mode:</strong> If we derive a sub class from a Private base class. Then both public member and protected members of the base class will become Private in derived class. 

- For Public:

### Code
```
// C++ program to demonstrate implementation
// of Inheritance

#include <bits/stdc++.h>
using namespace std;

//Base class
class Parent
{
	public:
	int id_p;
};

// Sub class inheriting from Base Class(Parent)
class Child : public Parent
{
	public:
	int id_c;
};

//main function
int main()
{
	
		Child obj1;
		
		// An object of class child has all data members
		// and member functions of class parent
		obj1.id_c = 7;
		obj1.id_p = 91;
		cout << "Child id is " << obj1.id_c << endl;
		cout << "Parent id is " << obj1.id_p << endl;
		
		return 0;
}
```

### Output
```
Child id is 7
Parent id is 91
```

- Summary:

![](https://media.geeksforgeeks.org/wp-content/cdn-uploads/table-class.png)

## 5. Types of Inheritance in C++

- <strong>Single Inheritance:</strong>  one sub class is inherited by one base class only.

![](https://media.geeksforgeeks.org/wp-content/uploads/single-inheritance.png)

- <strong>Multiple Inheritance:</strong> one sub class is inherited from more than one base classes.

![](https://media.geeksforgeeks.org/wp-content/uploads/multiple-inheritance.png)

### Syntax
```
class subclass_name : access_mode base_class1, access_mode base_class2, ....
{
  //body of subclass
};
```

- <strong>Multilevel Inheritance:</strong>  In this type of inheritance, a derived class is created from another derived class.

![](https://media.geeksforgeeks.org/wp-content/uploads/multilevel-inheritance.png)

- <strong>Hierarchical Inheritance:</strong> more than one derived class is created from a single base class.

![](https://media.geeksforgeeks.org/wp-content/uploads/hierarchical-inheritance.png)

- <strong>Hybrid (Virtual) Inheritance:</strong>  Hybrid Inheritance is implemented by combining more than one type of inheritance.

![](https://media.geeksforgeeks.org/wp-content/uploads/Hybrid-Inheritance.png)
