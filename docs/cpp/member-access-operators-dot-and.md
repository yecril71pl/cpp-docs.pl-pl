---
title: Operatory dostępu do elementów członkowskich:. i&gt;
ms.date: 11/04/2016
f1_keywords:
- .
- ->
helpviewer_keywords:
- member access, expressions
- operators [C++], member access
- dot operator (.)
- -> operator
- member access, operators
- postfix operators [C++]
- . operator
- member access
ms.assetid: f8fc3df9-d728-40c5-b384-276927f5f1b3
ms.openlocfilehash: 05bab55e1646783e0f8ab9b414d608c912f60a0f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178018"
---
# <a name="member-access-operators--and--gt"></a>Operatory dostępu do elementów członkowskich:. i&gt;

## <a name="syntax"></a>Składnia

```
postfix-expression . name
postfix-expression -> name
```

## <a name="remarks"></a>Uwagi

Operatory dostępu do elementów członkowskich **.** i **->** są używane do odwoływania się do elementów członkowskich struktur, Unii i klas. Wyrażenia dostępu do składowych mają wartość i typ wybranego elementu członkowskiego.

Istnieją dwa formy wyrażeń dostępu do składowych:

1. W pierwszej postaci *wyrażenie przyrostkowe* reprezentuje wartość typu struct, Class lub Union, a *Nazwa* nazwy składowej określonej struktury, Unii lub klasy. Wartość operacji to *Nazwa* i jest l-wartością, jeśli *przyrostke wyrażenie* jest l-wartością.

1. W drugiej postaci *wyrażenie przyrostkowe* reprezentuje wskaźnik do struktury, Unii lub klasy, a *Nazwa* nazwy składowej określonej struktury, Unii lub klasy. Wartość jest równa wartości *name* i jest l-wartością. Operator **->** odwołuje wskaźnik. W związku z tym wyrażenia `e->member` i `(*e).member` (gdzie *e* reprezentuje wskaźnik) dają identyczne wyniki (z wyjątkiem sytuacji, gdy operatory **->** lub <strong>\*</strong> są przeciążone).

## <a name="example"></a>Przykład

Poniższy przykład ilustruje obie formy operatora dostępu do elementu członkowskiego.

```cpp
// expre_Selection_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Date {
   Date(int i, int j, int k) : day(i), month(j), year(k){}
   int month;
   int day;
   int year;
};

int main() {
   Date mydate(1,1,1900);
   mydate.month = 2;
   cout  << mydate.month << "/" << mydate.day
         << "/" << mydate.year << endl;

   Date *mydate2 = new Date(1,1,2000);
   mydate2->month = 2;
   cout  << mydate2->month << "/" << mydate2->day
         << "/" << mydate2->year << endl;
   delete mydate2;
}
```

```Output
2/1/1900
2/1/2000
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia przyrostków](../cpp/postfix-expressions.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Klasy i struktury](../cpp/classes-and-structs-cpp.md)<br/>
[Składowe struktury i złożenia](../c-language/structure-and-union-members.md)
