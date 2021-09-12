# Interview Question

## Q.1 Why object oriented programming ? Explain importance of class, object with sample code.
- Object-oriented programming aims to implement real-world entities like inheritance, hiding, polymorphism etc in programming. The main aim of OOP is to bind    
  the data and the functions that operating on them together, so that no other part of the code can access this data except that function.
  
- OOP is faster and easier to execute.
- It provides a clear structure for the programs.
- It helps to make the code easier to maintain, modify and debug.
- Also provides reusablity of the code. 

### i. <strong>Importance of Class and Objects:</strong>
- Class serves as a template for creating or instantiating specific objects within a program. We can create mulitple objects using a single class.
- Objects is a basic unit of Object-Oriented Programming and represents the real life entities. They consist of state -> It is represented by attributes of an    
  object., behaviour -> It is represented by methods of an object., Identity -> Unique name to interact with other objects.
  
For an eg: 
```
#include <iostream>
using namespace std;

class person
{
    string name;
    int age;
public:
  void setdetails(string name, int age){
    this->name = name;
    this->age = age;
  }
    void getdetails(){
    cout << name <<" "<< age;
  }
};

int main()
{
  person p1; // p1 is a object
  p1.setdetails("bhavesh", 21);
  p1.getdetails();
}
```

## Q.2. Explain inheritance with example.
- Ability of a class to inherit properties from another class is called as inheritance. We a sub class/ Derived class which inherits properties from a base class/super class.
### Eg:
```
#include <iostream>
using namespace std;

class animal {

public:

  void sleep() {
    cout << "Animal Sleeps";
  }

  void eat() {
    cout << "Animal Eats";
  }
};

class dog: public animal {

public:
  void bark() {
    cout << "Dog Barks";
  }
};

int main()
{
  dog maku;

  maku.bark();
  maku.eat();
  maku.sleep();
}
```

## Q.3. Explain various type of access specifier(private, protected, public) with inheritance(private, protected, public). 
- Access specifiers are used to implement most important aspect of OOP that is Data Hiding. There are 3 access Specifiers in c++. i.e Public, Private, and Protected.

- When the data members and member function of a class are declared under public specifier, then they can be accessed by other classes and functions too in the program by using direct member access operator(.) with the object of that class.

- When the data members and member function of a class are declared under private specifier, then they can be accessed by the members of that class only. Also we a sub class cannot directly access private members of a super class. We have to use Friend Function to access the private members.

- Protected is similar to private specifier. But for data members and member function declared as protected in a class can be directly accessed by its derived class.

## Q.4. Explain how inheritance increases re-usability and productivity of class.
- Give vehicle example.

## Q.5 What is Polymorphism. Explain how you achieve Run time and compile time polymorphism. Also write sample code for the same.
- The word Polymorphism means many forms. For an eg a man at the same time can have different charecteristics like a man can be a husband, a father, an employee.   So a single person posses different behaviour in different situations.
- In c++ there are two types of Polymorphism.i.e Run time and compile time polymorphism.
- The compile time polymorphism can be achieved by function overloading or by operator overloading.
- The runtime polymorphism is achieved by function overriding.

<strong>Function Overloading</strong>
```
#include <iostream>

using namespace std;

void print(int i) {
  cout << i << endl;
}

void print(double i){
  cout << i << endl;
}

int main() {
  
  print(10);
  print(10.5);
  return 0;
}
```

<strong>Operator Overloading</strong>
```
#include <iostream>

using namespace std;

class test {
  int count;
public:
  test(int c) {
    count = c;
  }
  
  void operator --(){
    count = count - 3;
  }
  
  void display() {
    cout << count << endl;
  }
};

int main() {
  test t1(10);
  --t1;
  t1.display();
}
```

<strong>Function Overriding</strong>
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

## Q.6. Explain the order in which constructor and destructor will be called in multilevel inheritance with sample code.
- ![](https://media.geeksforgeeks.org/wp-content/uploads/order-of-constructor.png)
