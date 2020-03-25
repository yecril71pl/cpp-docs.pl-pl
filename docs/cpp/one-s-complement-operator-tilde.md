---
title: 'Operator&#39;uzupełnienia s: ~'
ms.date: 11/04/2016
f1_keywords:
- "~"
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
ms.openlocfilehash: 777f253925caf38647863bdaa93fde8d5a03e3f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177719"
---
# <a name="one39s-complement-operator-"></a>Operator&#39;uzupełnienia s: ~

## <a name="syntax"></a>Składnia

```
~ cast-expression
```

## <a name="remarks"></a>Uwagi

Operator dopełnienia (`~`), czasami nazywany operatorem "deuzupełnienie", daje bitową część tego operandu. Oznacza to, że każdy bit, który jest 1 w operandzie, ma wartość 0 w wyniku. Z kolei każdy bit, który jest równy 0 w operandzie, ma wartość 1 w wyniku. Operand do operatora dopełnienia musi być typem całkowitym.

## <a name="operator-keyword-for-"></a>Słowo kluczowe operatora dla ~

Operator **zgodności** jest odpowiednikiem tekstu `~`. Istnieją dwa sposoby uzyskania dostępu do operatora **zgodności** w programach: Dołącz plik nagłówka `iso646.h`lub skompiluj z [/za](../build/reference/za-ze-disable-language-extensions.md).

## <a name="example"></a>Przykład

```cpp
// expre_One_Complement_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main () {
   unsigned short y = 0xFFFF;
   cout << hex << y << endl;
   y = ~y;   // Take one's complement
   cout << hex << y << endl;
}
```

W tym przykładzie nowa wartość przypisana do `y` jest uzupełnieniem jednego z wartości bez znaku lub 0x0000.

Promocja całkowa jest wykonywana na całkowitych operandach, a wynikowy typ to typ, do którego zostanie podwyższony operand. Zobacz [standardowe konwersje](standard-conversions.md) , aby uzyskać więcej informacji na temat sposobu przeprowadzania promocji.

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Jednoargumentowe operatory arytmetyczne](../c-language/unary-arithmetic-operators.md)
