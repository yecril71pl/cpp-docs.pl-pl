---
title: 'Operator logiczny negacji: !'
ms.date: 08/27/2018
f1_keywords:
- '!'
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: 06142ef15fcdbafdbae4b892772a04b117c087f6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446539"
---
# <a name="logical-negation-operator-"></a>Operator logiczny negacji: !

## <a name="syntax"></a>Składnia

```
! cast-expression
```

## <a name="remarks"></a>Uwagi

Operator logiczny negacji ( **!** ) odwraca znaczenie jego operandu. Argument operacji musi być typu arytmetycznego lub wskaźnika (lub wyrażenia, które ma wartość arytmetyczną lub typu wskaźnika). Operand jest niejawnie konwertowany na typ **bool**. Wynik ma wartość TRUE, jeśli przekonwertowany operand ma wartość FALSE; wynik ma wartość FAŁSZ, jeśli przekonwertowany operand ma wartość TRUE. Wynik jest typu **bool**.

W przypadku wyrażenia *e*wyrażenie jednoargumentowe `!e` jest równoważne wyrażeniu `(e == 0)`, z wyjątkiem przypadków, w których są wykorzystywane przeciążone operatory.

## <a name="operator-keyword-for-"></a>Słowo kluczowe operatora dla!

Operator **not** jest alternatywną pisownią **!** . Istnieją dwa sposoby uzyskania dostępu do operatora **not** w programach: Dołącz plik nagłówka \<iso646. h > lub skompiluj z opcją kompilatora [/za](../build/reference/za-ze-disable-language-extensions.md) (Disable Language Extensions).

## <a name="example"></a>Przykład

```cpp
// expre_Logical_NOT_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    if (!i)
        cout << "i is zero" << endl;
}
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Jednoargumentowe operatory arytmetyczne](../c-language/unary-arithmetic-operators.md)<br/>
