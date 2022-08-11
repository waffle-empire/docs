# Getting started

### Commit convention
Types:
- feat: The new feature you're adding to a particular application
- fix: To fix a bug
- style: Feature and updates related to styling
- refactor: Refactoring a specific section of the codebase
- test: Everything related to testing
- docs: Everything related to documentation
- chore: Regular code maintanance

A scope is a phrase descibing parts of the code affected by the changes. For example "(userservice)"

Body (optional) can provide additional contextual information. For breaking changes the body MUST start with "BREAKING CHANGE".

Footer (optional) is used to reference issues effected bt the code changes. For example "Fixes #13". Can also be used to indicate breaking changes by starting with "BREAKING CHANGE".
#### Structure


```
<type>(scope): <description>

[optional body]

[optional footer]
```

#### Examples
- `feat(order): add purchase order button`
- `docs(readme): document coding conventions`


# C++ Coding Standards Blue Waffle Empire
## Naming Style

| Entities | Naming | Preview |
| ----------- | ----------- | ---------- |
| NameSpaces | UpperCamelCase | namespace `ExNamespace` |
| Classes and Structs | UpperCamelCase | Class `ExClass` |
| Enums | UpperCamelCase | Enum `ExEnum` |
| Enum Members | ALL_UPPER | ExNum::`NONE`; ExNum::`FIRST_HALF`; ...
| Global Variables| gUpperCamelCase | bool `gRunning` |
| Macros | ALL_UPPER | #define `USE_OPENGL` |
| Template Parameter | UpperCamelCase | Template<`class T`> |
| Parameters | lowerCamelCase / pUpperCamelCase | ExMethod(int `number`, int* `pNumber`) |
| Local Variables | lowerCamelCase / pUpperCamelCase | {int `number{}`;<br> int* `pNumber`{ new int{}}} |
| Member Variables | m_ / m_p / m_v + UpperCamelCase | int `m_Number`;<br> int* `m_pNumber`;<br> std::vector<int> `m_vNumbers`; |
| Member Methods | UpperCamelCase | void `ExMethod`(int param1, int param2); |

<br><br><br>

## Formatting Style
### **Indents**
prefer Tabs for indents

### **Braces**  

With `if` statenebts and `for` loops we drop the brackets if it only has to execute 1 line of code or if it calls a method
```c++
if (true)
    ExecuteMethod();

int num;
if (true)
    num += 5;

for (;;)
    ExecuteMethod();

for (;;)
    num += 5;
```


Example for namespaces, classes, etc...
```c++
namespace ExNamespace
{
    class ExClass
    {
    public:
        ExClass()
        {
        }

        ExMethod();

        GetNum() const 
        {
            return m_Num;
        }
    private:
        int m_Num;
    }
}

ExNamespace::ExClass::ExMethod()
{
    auto lambda = []()
    {
        int x = 0;
        return x;
    };

    switch (expression)
    {
    case 0:
    {
        // do stuff
        break;
    }
    case 1:
    {
        // do stuff
        break;
    }
    }
    
    do
    {
        // do stuff
    } while (true);
}
```
### **Guarding if statements**  

Prefer using guarding `if` statements for readability

Bad Example:
```c++ 
void Method()
{
    bool val1 = true;
    bool val2 = false;
    bool val3 = true;

    if(val1)
    {
        if(val2)
        {
        }
        else 
        {
            if(val3)
            {
                // code part
                // where tf are we at
            }
        }
    }
}
```

Guarded if Example:
```c++
void Method()
{
    bool val1 = true;
    bool val2 = false;
    bool val3 = true;

    if(!val1)
        return;

    if (val2)
        return;

    if (!val3)
        return;

    // here comes the code part
}
```

### **Member variables in classes**

1. Seperate every variable to a single line
2. Initialize all member variables
3. Use the same order of initialization as in the header file
4. Order data types from big to low 

```c++
// Header File
class ExClass
{
public:
    ExClass();

private:
    float m_Length;
    int m_Number;
    bool m_Enabled;
}

// Cpp File
ExClass::ExClass()
    : m_Length{ 1.f }
    , m_Number{ 5 }
    , m_Enabled { true }
    {
    }
```
