# Object Oriented Programing (Interview Prep) (Part-II)

## 1. Difference between object and class?
**No**|**Object**|**Class**
:-----:|:-----:|:-----:
1|Object is an instance of a class.|Class is a blueprint or template from which objects are created.
2|Object is a real world entity such as pen, laptop, mobile, bed, keyboard, mouse, chair etc.|Class is a group of similar objects.
3|Object is a physical entity.|Class is a logical entity.
4|Object is created through new keyword mainly e.g.Student s1=new Student();|Class is declared using class keyword e.g.class Student{}
5|Object is created many times as per requirement.|Class is declared once.
6|Object allocates memory when it is created.|Class doesn't allocated memory when it is created.
7|There are many ways to create object in java such as new keyword, newInstance() method, clone() method, factory method and deserialization.|There is only one way to define class in java using class keyword.


## 2. Static Keyword?
### Static keyword has different meanings when used with different types. We can use static keyword with:

### 1. Static variables in a Function
- When a variable is declared as static, space for it gets allocated for the lifetime of the program. Even if the function is called multiple times, space for the static variable is allocated only once and the value of variable in the previous call gets carried through the next function call. 
- i.e The variables declared as static are <strong>initialized only once</strong>.

### Code

```
#include <bits/stdc++.h>

using namespace std;

void nonstatic() {

    int k = 0;

    cout << k << " " << &k << endl;

    k++;
}

void isstatic() {

    static int k = 0;

    cout << k << " " << &k << endl;

    k++;

}

int main() {

    for(int i = 0; i < 5; i++) {
        nonstatic();
    }

    cout << "-------------" << endl;

    for(int i = 0; i < 5; i++) {
        isstatic();
    }

    return 0;
}
```

### Output

```
0 0x16b4d799c
0 0x16b4d799c
0 0x16b4d799c
0 0x16b4d799c
0 0x16b4d799c
-------------
0 0x10493003c
1 0x10493003c
2 0x10493003c
3 0x10493003c
4 0x10493003c
```

### 2. Static variables in a class
- The static variables in a class are shared by the objects. There can not be multiple copies of same static variables for different objects.
- Also because of this reason static variables can not be initialized using constructors.


### Code

```
// C++ program to demonstrate static
// variables inside a class

#include<iostream>
using namespace std;

class GfG
{
public:
	static int i;
	
	GfG()
	{
		// Do nothing
	};
};

int main()
{
GfG obj1;
GfG obj2;
obj1.i =2;
obj2.i = 3;
	
// prints value of i
cout << obj1.i<<" "<<obj2.i;
}
```

### Output

```
/tmp/ccWVNtqh.o: In function `main':
d3bb40b0d80d4e6454fe41d94e57e635.cpp:(.text+0x32): undefined reference to `GfG::i'
d3bb40b0d80d4e6454fe41d94e57e635.cpp:(.text+0x3c): undefined reference to `GfG::i'
d3bb40b0d80d4e6454fe41d94e57e635.cpp:(.text+0x46): undefined reference to `GfG::i'
d3bb40b0d80d4e6454fe41d94e57e635.cpp:(.text+0x4c): undefined reference to `GfG::i'
collect2: error: ld returned 1 exit status
```

### Code

```
#include <bits/stdc++.h>

using namespace std;

class ID {

public:

    static string prefix;

    string suffix, name;

    ID(string stname, string suff){

        suffix = suff;
        name = stname;
    }

    void printId(){

        cout << name << " " << ":" << " " << prefix+suffix << endl;

    }
};

string ID::prefix = "XIE";

int main() {

    ID bhavesh("Bhavesh", "EXTC181959");
    ID vikas("Vikas", "IT181914");

    bhavesh.printId();
    vikas.printId();

    return 0;
}
```

### Output

```
Bhavesh : XIEEXTC181959
Vikas : XIEIT181914
```

### 3. Class objects as static
- Just like variables, objects also when declared as static have a scope till the lifetime of program.

### Code

```
// CPP program to illustrate
// when not using static keyword
#include<iostream>
using namespace std;

class GfG
{
	int i;
	public:
		GfG()
		{
			i = 0;
			cout << "Inside Constructor\n";
		}
		~GfG()
		{
			cout << "Inside Destructor\n";
		}
};

int main()
{
	int x = 0;
	if (x==0)
	{
		GfG obj;
	}
	cout << "End of main\n";
}
```

### Output

```
Inside Constructor
Inside Destructor
End of main
```

- In the above program the object is declared inside the if block as non-static. So, the scope of variable is inside the if block only. 
- So when the object is created the constructor is invoked and soon as the control of if block gets over the destructor is invoked as the scope of object is inside the if block only where it is declared.


### Code

```
// CPP program to illustrate
// class objects as static
#include<iostream>
using namespace std;

class GfG
{
	int i = 0;
	
	public:
	GfG()
	{
		i = 0;
		cout << "Inside Constructor\n";
	}
	
	~GfG()
	{
		cout << "Inside Destructor\n";
	}
};

int main()
{
	int x = 0;
	if (x==0)
	{
		static GfG obj;
	}
	cout << "End of main\n";
}
```

### Output

```
Inside Constructor
End of main
Inside Destructor
```
- Now the destructor is invoked after the end of main. This happened because the scope of static object is through out the life time of program.


### 4. Static functions in a class
- Just like the static data members or static variables inside the class, static member functions also does not depend on object of class.
- <strong>We are allowed to invoke a static member function using the object and the ‘.’ operator but it is recommended to invoke the static members using the class name and the scope resolution operator.</strong>
- <strong>Static member functions are allowed to access only the static data members or other static member functions, they can not access the non-static data members or member functions of the class.</strong>


### Code

```
// C++ program to demonstrate static
// member function in a class
#include<iostream>
using namespace std;

class GfG
{
public:
	
	// static member function
	static void printMsg()
	{
		cout<<"Welcome to GfG!";
	}
};

// main function
int main()
{
	// invoking a static member function
	GfG::printMsg();
}
```

### Output

```
Welcome to GfG!
```
