---
title: bad_typeid — wyjątek
ms.date: 10/04/2019
f1_keywords:
- bad_typeid
- bad_typeid_cpp
helpviewer_keywords:
- bad_typeid exception
- exceptions [C++], bad_typeid
ms.assetid: 5963ed58-4ede-4597-957d-f7bbd06299c2
ms.openlocfilehash: bb56de77ba001b5a511ef3a2695d18109b1ed3ca
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245916"
---
# <a name="bad_typeid-exception"></a>bad_typeid — wyjątek

Wyjątek **bad_typeid** jest generowany przez [operatora typeid](../cpp/typeid-operator.md) , gdy operand dla elementu **typeid** jest wskaźnikiem o wartości null.

## <a name="syntax"></a>Składnia

```
catch (bad_typeid)
   statement
```

## <a name="remarks"></a>Uwagi

Interfejs dla **bad_typeid** jest:

```cpp
class bad_typeid : public exception
{
public:
   bad_typeid();
   bad_typeid(const char * _Message = "bad typeid");
   bad_typeid(const bad_typeid &);
   virtual ~bad_typeid();

   bad_typeid& operator=(const bad_typeid&);
   const char* what() const;
};
```

Poniższy przykład przedstawia operator **typeid** , który zgłasza wyjątek **bad_typeid** .

```cpp
// expre_bad_typeid.cpp
// compile with: /EHsc /GR
#include <typeinfo>
#include <iostream>

class A{
public:
   // object for class needs vtable
   // for RTTI
   virtual ~A();
};

using namespace std;
int main() {
A* a = NULL;

try {
   cout << typeid(*a).name() << endl;  // Error condition
   }
catch (bad_typeid){
   cout << "Object is NULL" << endl;
   }
}
```

## <a name="output"></a>Dane wyjściowe

```Output
Object is NULL
```

## <a name="see-also"></a>Zobacz także

[Informacje o typie w czasie wykonywania](../cpp/run-time-type-information.md)\
[Słowa kluczowe](../cpp/keywords-cpp.md)
