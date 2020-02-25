# C++

Useful command

```
> g++ fileToCompile.cpp -o compiledFileName -std=c++17 -O3 -Wall
> cat input.txt | ./c_file_compiled > output.txt
> zip folderZipName.zip file1 file2 folder1 -x "output" // exclude output folder form zip while zipping file1 file2 and folder1
```

## Index

### Library

- [iostream](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#iostream)
- [string](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#string)
- [vector](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#vector)
- [map](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#map)
- [queue](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#queue--fifo-list)
- [stack](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#stack--lifo-list)
- [heap](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#heap)
- [bitset](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#bitset)
- [algorithms](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#algorithms)
- [cmath](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#cmath)
- [fstream](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#fstream)

### More

- [break vs continue](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#break-vs-continue)
- [function overloading](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#function-overloading)
- [class | OOP](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#class--oop)
- [time execution](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#a-tracker-for-time-execution)
- [get input from terminal](https://github.com/zhou0998/Nice2Know/blob/master/C%2B%2B/README.md#input-from-terminal)

## iostream

```c++
#include<iostream>
int a = 10;
cout << "Hello!" << a;
cin >> a; //like scanf("%d", &a) of c
```

## string

```c++
#include<string>

string str,str2;
getline(cin,str); // take string with whitespace until \n
cin >> str; // take string until whitespace
cout << str;
str.push_back('s'); // add a char at the end of string
str.pop_back(); // remove last char of string
str.resize(10); //resize length of string
str.length(); //return length of string
for(auto i = str.begin(); i != str.end(); i++) //exist also rbegin and rend, and i++ remain
    cout << *i;
str.swap(str2); // swap 2 string
```

## vector

```c++
#include<vector>

vector<type> name_var;

name_var.push_back(another_var_of_type);

for(auto iter = name_var.begin(); iter != name_var.end(); iter++)
    cout << *iter;

// same of previously but reverset from end to start
for(auto iter = name_var.rbegin(); iter != name_var.rend(); iter++)
    cout << *iter;
```

- **.size()** # of elements on the array
- **.resize(n)** change the size of the array to n
- **.empty()** return true/false if the array is empty or not
- **.swap(another_vector)** swap 2 vector same size and type
- via **[ ]** as a normal array
- **.front()** return first element
- **.back()** return last element
- **.push_back(a)** add to the end element a
- **.pop_back()** _remove_ last element of the array
- **.insert(name_var.begin() + pos, a)** insert element a to a certain position via pointer
- **.erase(name_var.begin() + pos)** remove a certain element via pointer  
   also a range: .erase(name_var.begin() + pos1, name_var.begin() + pos2)
- **.clear()** delete all element of the array

## map

```c++
#include<map>

map<int, int> my_map = {{1, 1}, {0, 3}}; //<key, value>
my_map.insert(10);

for(auto iter = my_map.begin(); iter != my_map.end(); iter++)
    cout << *iter;
// create a new map with element of previous one
map<int, int> my_map_2(my_map.begin(), my_map.end());
```

- **.erase(x)** remove a certain element via key x
- **.find(x)** return pointer to key x if it exist, if it doesn't return a pointer to end
- **.lower_bound(x)** return pointer to a element with a key <= than x
- **.upper_bound(x)** return pointer to a element with a key > than x
- **.empty()** return true/false if the map is empty or not
- **.clear()** delete all element of the map

## queue | FIFO list

```c++
#include<queue>

queue<int> my_queue;
```

- **.empty()** return true/false if it is empty or not
- **.push(x)** insert x on the FIFO
- **.pop()** remove the element with FIFO policy
- **.size()** return size of the list
- **.front()** return references to first element without remove it
- **.back()** return references to last element without remove it

## stack | LIFO list

```c++
#include<stack>

stack<int> my_queue;

```

- **.empty()** return true/false if it is empty or not
- **.push(x)** insert x on the LIFO
- **.pop()** remove the element with LIFO policy
- **.size()** return size of the list
- **.top()** return references to first element without remove it(most top)

## heap

It is created from a vector and using algorithms function

```c++
vector<int> v1
for(auto &x : v1)
    cout << x;
```

- **make_heap(start ref, end ref, lambda for heap func or nothing)** create a heap with vector
- **is_heap(start ref, end ref, lambda for heap func or nothing)** return true or false if it is or not a heap
- **push_heap(start ref, end ref, lambda for heap func or nothing)**
  **before you need to .push_back() a element** and then execute this function throug all the vector
- **pop_heap(start ref, end ref, lambda for heap func or nothing)** move root element to end
  - **.pop_back()** delete and resize last element of list
- **sort_heap(start ref, end ref, lambda for heap func or nothing)**
- **.front()** root element
- **.back()** last element of list

```c++
class interClass
{
private:
    int x;

public:
    interClass() : x(rand() % 1000){};
    void printNum()
    {
        cout << x << endl;
    }
    int getX() { return x; }
};
auto comp(interClass *c1, interClass *c2) { return c1->getX() > c2->getX(); } //true se deve cambiare il root, ora ottengo come minimo al root
int main()
{
    vector<interClass *> a(10);
    for (auto &x : a)
        x = new interClass();
    for (auto &x : a)
        x->printNum();
    make_heap(a.begin(), a.end(), &comp);
    cout << endl;
    for (auto &x : a)
        x->printNum();
    cout << endl;
    while (a.size())
    {
        a.front()->printNum();
        pop_heap(a.begin(), a.end(), &comp);
        a.pop_back();
    }
}
```

## bitset

```c++
#include<bitset>
#define M 30

bitset<M> bset1;
bitset<M> bset2(1234); // convert 1234 to binary
bitset<M> bset3(string("1100"));
bset1.reset();

```

- access via **[ ]** as a normal array
- **.count()** return # of 1 on the bitset
- **.size()** return size of the bitset
- **.any()** at least one set, return true or false
- **.all()** if all are one, return true or false
- **.none()** if all zero, return true or false
- **.set()** set all to one
  - .set(n) set n pos to one
  - .set(n, 0 or 1) set n pos to 0 or 1
- **.reset()** make all zero
- **.flip()** invert all value

Operation

- **==** true or false if equal
- **!=** true or false if not equal
- **^** xor, 1 if different and 0 if equal
- **&** and
- **|** or
- **>> n** or **<< n** shit to left or right of n position

## algorithms

```c++
#include<vector>
#include<algorithm>
vector<int> to_test
if(all_of(to_test.begin(), to_test.end(), [](int i){return i % 2 == 0;})) // (start reference, end reference, function to apply(if inline function it have to be a lambda so start with [], otherwise you can put a function name))
    cout << "All numbers are even\n"
```

Non-modifying sequence operations:

- **all_of(start ref, end ref, lambda)** test if all element of a vector respect the function
- **any_of(start ref, end ref, lambda)** test if at least one element of a vector respect the function
- **none_of(start ref, end ref, lambda)** test if all element of a vector doesn't respect the function
- **for_each(start ref, end ref, lambda)** same syntax of previous, if the function take a reference it can modify value of the object
- **find(start ref, end ref, x)** return the first reference equal to _X_, it doesn't take a function
  - **find_if(start ref, end ref, lambda)** instead a value it takes a function and return the first reference that return true
  - **find_if_not(start ref, end ref, lambda)** instead a value it takes a function and return the first reference that return false
- **count(start ref, end ref, x)** count how many _X_ are present on the vector
  - **count_if(start ref, end ref, lambda)** count how many satisfy the lambda function

Modifying sequence operations:

- **copy(start ref, end ref, start 2nd ref vector)** copy value of first vector to second one
  - **copy_n(start ref, #pos, start 2nd ref vector)**
  - **copy_if(start ref, end ref, start 2nd ref vector, lambda)**
  - **copy_backwards(start ref, #pos, start 2nd ref vector)** if copy from end to start, so the start of 2nd is like where the copied value have to end
- **remove(start ref, end ref, x)** remove element if equals same syntak of _.find()_
  - **remove_if(start ref, end ref, lambda)**
- **fill(start ref, end ref, x)** fill with a certain value _X_ a range
  - **fill_n(start ref, #pos, x)** instead of end reference I use a number position in according with the start reference

Some Algorithms:

- **sort(start ref, end ref, optional lambda or nothing())**
- **is_sorted(start ref, end ref)**
- **lower_bound(start ref, end ref, x)** return <= to x, the nearest
- **upper_bound(start ref, end ref, x)** return > to x, the nearest
- **binary_search(start ref, end ref, x)** it checks only if it exist, for ref search see lower_bound or upper_bound
- **reverse(start ref, end ref)** reverse the vector
- **swap(vector A, vector B)** swap A B content value

Merge(sorted vector):

- **merge(start 1st ref, end 1st ref, start 2nd ref, end 2nd ref, start 3nd ref)** merge 2 sorted vector on another vector
- **set_union(start 1st ref, end 1st ref, start 2nd ref, end 2nd ref, start 3nd ref)** return on 3nd vector a union set of two vector
- **set_intersection(start 1st ref, end 1st ref, start 2nd ref, end 2nd ref, start 3nd ref)** return on 3nd vector a intersection set of two
- **set_difference(start 1st ref, end 1st ref, start 2nd ref, end 2nd ref, start 3nd ref)** return on 3nd vector a difference of 1st - 2nd

_all returned result are sorted and certain also a set(so no repeted element)_

## cmath

- **abs(x)** Returns the absolute value of x
- **acos(x)** Returns the arccosine of x, in radians
- **asin(x)** Returns the arcsine of x, in radians
- **atan(x)** Returns the arctangent of x, in radians
- **cbrt(x)** Returns the cube root of x
- **ceil(x)** Returns the value of x rounded up to its nearest integer
- **cos(x)** Returns the cosine of x, in radians
- **cosh(x)** Returns the hyperbolic cosine of x, in radians
- **exp(x)** Returns the value of Ex
- **expm1(x)** Returns ex -1
- **fabs(x)** Returns the absolute value of a floating x
- **fdim(x, y)** Returns the positive difference between x and y
- **floor(x)** Returns the value of x rounded down to its nearest integer
- **hypot(x, y)** Returns sqrt(x2 +y2) without intermediate overflow or underflow
- **fma(x, y, z)** Returns x\*y+z without losing precision
- **fmax(x, y)** Returns the highest value of a floating x and y
- **fmin(x, y)** Returns the lowest value of a floating x and y
- **fmod(x, y)** Returns the floating point remainder of x/y
- **pow(x, y)** Returns the value of x to the power of y
- **sin(x)** Returns the sine of x (x is in radians)
- **sinh(x)** Returns the hyperbolic sine of a double value
- **tan(x)** Returns the tangent of an angle
- **tanh(x)** Returns the hyperbolic tangent of a double value

- **round(x)** x rounded to the nearest integral
  - 2.y => 2 with y in [0,4]
  - 2.y => 3 with y in [5,9]
- **ceil(x)** x rounded to the highest integral
  - 2.y => 3 with y in [1,9]
- **floor(x)** x rounded to the lowest integral
  - 2.y => 2 with y in [1,9]
- **trunc(x)** take x integral part
  - z.y => z with y in [0,9]

## fstream

Main Object:

1. **ofstream**, only write
2. **ifstream**, only read
3. **fstream**, both

```c++
#include <iostream>
#include <fstream>
using namespace std;

int main () {
  ofstream myfile;
  myfile.open ("example.txt");
  myfile << "Writing this to a file.\n"; // so read is with myfile >> inputVar; also for string but in this case it will end at first whitespace or \n
  myfile.close();
  return 0;
}
```

- **.open(filename, flag)** flag can be
  - **ios :: in** set read mode
  - **ios :: out** set write mode
  - **ios :: ate** the cursor will start at the beginning of the file
  - **ios :: app** the cursor will start at the end of the file
  - **ios :: trunc** if file exist, will overwrite it
    ex. _ofstream myfile ("example.bin", ios::out | ios::app | ios::binary);_
- **getline(fstream object, string variable)** take a entile line to the \n

## Class | OOP

```c++
class Animal {
  private:
    // NOT ACCESSIBLE from CLASS DERIVED
    int age, id; // NOT ACCESSIBLE from class derived
    string name;
  public:
    // ACCESSIBLE from EVERYWHERE and EVERYONE
    Animal(string name): name(name), age(0) {
      cout << "New animal created" << endl;
    };
    int getAge(){
      return age;
    }
    void makeSound();
  protected:
    // ACCESSIBLE from CLASS DERIVED
    int otherVar;
};

class Combact {
  private:
    int damage;
  public:
    Combat(int d): damage(d) {};
    int getDamage(){
      return damage;
    }
}

void Animal :: makeSound(){
  cout << "Wof Wof" << endl;
}

class CombactAnimal : public Animal, public Combact{
  private:
    int seriesCode;
  public:
    CombactAnimal(string name, int damage, int seriesCode): seriesCode(seriesCode), Combact(damage), Animal(name) {};
    int getDamage(){
      return damage * 2;
    }
}

Animal a = Animal("Star"); // a is a object of Animal
Animal *b = new Animal("Star 2"); // b is a pointer to a object Animal
```

## Break vs Continue

Terminate for loop at `i == 4`

```c++
for (int i = 0; i < 10; i++)
{
  if (i == 4)
    break;
  cout << i << endl;
}
```

Jump to next loop when `i == 4`

```c++
for (int i = 0; i < 10; i++)
{
  if (i == 4)
    continue;
  cout << i << endl;
}
```

## Function Overloading

I can have multiple function with same name, but different parameters

```c++
int myFunc(int x);
float myFunc(float x);
double myFunc(double x, double y);
```

## A Tracker for Time Execution

```c++
using namespace std;
using namespace std::chrono;

class Tracker
{
private:
    time_point<system_clock> start, end;
    string name;
    int counter;

public:
    Tracker(string name = "") : name(name), counter(0){};
    void setName(string name)
    {
        this->name = name;
    }
    void resetCounter()
    {
        counter = 0;
    }
    void Start()
    {
        start = system_clock::now();
        counter++;
    }
    void Lap(string name = "")
    {
        end = system_clock::now();
        PrintAll();
        if (name == "")
        {
            counter++;
            start = system_clock::now();
            return;
        }
        cout << endl;
        counter = 1;
        this->name = name;
        start = system_clock::now();
    }
    void Stop(int print = 1)
    {
        end = system_clock::now();
        if (print)
            PrintAll();
    }
    void PrintAll()
    {
        duration<double> elapsed_seconds = end - start;
        if (name != "")
            cout << name + " | ";
        cout << "Step " << counter << ") " << elapsed_seconds.count() << "s\n";
    }
    void Delta()
    {
        duration<double> elapsed_seconds = end - start;
        cout << "Delta: " << elapsed_seconds.count() << "s\n";
    }
};
```

## Input from Terminal

`> ./compiledFileName varToPass1 varToPass2`

```c++
int main( int argc, char* argv[] )
{
    string my_arg;

    // First argument is always the name of your program
    cout << argv[0] << endl;

    if( argc == 2 )
    {
        // Something has been passed in
        my_arg = argv[1];
        cout << "Argument passed in is " << my_arg << endl;
    }

    return 0;
}
```
