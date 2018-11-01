---
title: Operatory dostępu do składowych:. i -&gt;
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
ms.openlocfilehash: 0f370aa04af2e78efd5edfb7836fb71a4c4516a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468747"
---
# <a name="member-access-operators--and--gt"></a>Operatory dostępu do składowych:. i -&gt;

## <a name="syntax"></a>Składnia

```
postfix-expression . name
postfix-expression -> name
```

## <a name="remarks"></a>Uwagi

Operatory dostępu do składowych **.** i **->** służą do odwoływania się do elementów członkowskich struktury, Unii i klasy. Wyrażenia dostępu do składowych mają wartość i typ wybranego elementu członkowskiego.

Istnieją dwa rodzaje wyrażenia dostępu do składowych:

1. W pierwszej formie *wyrażeniem przyrostkowym* reprezentuje wartość struktury, klasy lub typ union i *nazwa* nazwy członka określonej struktury, Unii lub klasy. Wartością operacji jest *nazwa* i jest l wartością, jeśli *wyrażeniem przyrostkowym* jest l wartością.

1. W drugim formularzu *wyrażeniem przyrostkowym* reprezentuje wskaźnik do struktury, Unii lub klasy, i *nazwa* nazwy członka określonej struktury, Unii lub klasy. Wartość jest *nazwa* i jest l wartością. **->** Operator wyłuskania wskaźnika. W związku z tym, wyrażenia `e->member` i `(*e).member` (gdzie *e* reprezentuje wskaźnik) uzyskanie takie same wyniki (z wyjątkiem, gdy operatory **->** lub <strong>\*</strong> są przeciążone).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano oba rodzaje operator dostępu do elementu członkowskiego.

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

## <a name="see-also"></a>Zobacz także

[Wyrażenia przyrostków](../cpp/postfix-expressions.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Klasy i struktury](../cpp/classes-and-structs-cpp.md)<br/>
[Składowe struktury i złożenia](../c-language/structure-and-union-members.md)