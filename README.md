# docs

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


### C++ Class example
```cpp
#include "common.hpp"

#include <vector> 
                      // external includes always with angled brackets
namespace Exmpl
{
  using byte = unsigned char;
  enum class ExampleEnum      
  {                  // prefer enum class over enum! unless you need the regular enum functionality
    NONE,
    DEFAULT,
    SECOND,
    THIRD
  };

  class Network final
  {
  public:
                // all these methods should be put in the .cpp file

    Network()                // initialize all member variables
      : m_Length(4)
      , m_pData(new byte[64])
      , m_ThreadCount(8)
      , m_Type(eExampleEnum::DEFAULT)
    {

    }

    ~Network()
    {
      delete[] m_pData;
    }

    [[nodiscard]] std::vector<byte> GetCollectedData() // only use [[nodiscard]] on long and heavy methods, or methods that return a copy of a big data type
    {
        // do a lot of calcs here
    }

    byte* Data() const  // getters and setters can stay in .hpp file
    {
      return m_pData;
    }

    void SetType(ExampleEnum newType)
    {
      m_Type = newType;
    }
   private:
     int m_Length;   // use m_ prefix for member variables + UpperCamelCase
     byte* m_pData;  // use m_p prefix for pointer member variables + UpperCamelCase
    
     std::vector<byte> m_vCollectedData;   // optionally can use m_v prefix for arrays/lists/vectors + UpperCamelCase

    std::uint32_t m_ThreadCount;
    ExampleEnum m_Type;
  }
}
```