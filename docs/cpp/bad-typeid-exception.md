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
ms.openlocfilehash: 0389a6db1249ad47d4ca5cc10003169933c7a5c3
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331675"
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
   bad_typeid(const char * _Message = "bad typeid");
   bad_typeid(const bad_typeid &);
   virtual ~bad_typeid();
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