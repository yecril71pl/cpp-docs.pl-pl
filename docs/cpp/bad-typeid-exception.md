---
title: bad_typeid — Wyjątek
ms.date: 11/04/2016
f1_keywords:
- bad_typeid
- bad_typeid_cpp
helpviewer_keywords:
- bad_typeid exception
- exceptions [C++], bad_typeid
ms.assetid: 5963ed58-4ede-4597-957d-f7bbd06299c2
ms.openlocfilehash: 2ff7339b02cfe8c21cebfa7d9bb0cc98b3e08799
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68242262"
---
# <a name="badtypeid-exception"></a>bad_typeid — Wyjątek

**Bad_typeid** wyjątek jest generowany przez [typeid operator](../cpp/typeid-operator.md) gdy argument **typeid** jest wskaźnikiem typu NULL.

## <a name="syntax"></a>Składnia

```
catch (bad_typeid)
   statement
```

## <a name="remarks"></a>Uwagi

Interfejs **bad_typeid** jest:

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

W poniższym przykładzie przedstawiono **typeid** operator zgłaszanie **bad_typeid** wyjątku.

```cpp
// expre_bad_typeid.cpp
// compile with: /EHsc /GR
#include <typeinfo.h>
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

[Informacje o typach uzyskiwane w czasie rzeczywistym](../cpp/run-time-type-information.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)