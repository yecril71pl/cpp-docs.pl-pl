---
title: 'Jeden&#39;operatorem dopełnienia s: ~'
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
ms.openlocfilehash: d8fb8ca56932669ff85646f2aa0c10691122013b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469784"
---
# <a name="one39s-complement-operator-"></a>Jeden&#39;operatorem dopełnienia s: ~

## <a name="syntax"></a>Składnia

```
~ cast-expression
```

## <a name="remarks"></a>Uwagi

Operator dopełnienia jednostkowego (`~`), czasami nazywane operator "dopełnienia bitowego", daje bitowej, jeden na uzupełnienie swojego operandu. Każdego bitu, który ma wartość 1 w argumencie operacji jest 0, w wyniku. Z drugiej strony każdego bitu, który ma wartość 0 w argumencie operacji wynosi 1, w wyniku. Argument operacji do operator dopełnienia jednostkowego musi być typu całkowitego.

## <a name="operator-keyword-for-"></a>Operator — słowo kluczowe dla ~

**Compl** operator jest odpowiednikiem tekstu `~`. Istnieją dwa sposoby dostępu do **compl** operatora w programach: dołączanie pliku nagłówka `iso646.h`, lub kompilowanie z [/za](../build/reference/za-ze-disable-language-extensions.md).

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

W tym przykładzie nowa wartość przypisana do `y` to uzupełnienie jedynkowe 0xFFFF lub 0x0000 wartości bez znaku.

Promocja typu całkowitego odbywa się w przypadku argumentów operacji typu całkowitego, a wynikowy typ jest typem, do którego argument jest podnoszony. Zobacz [konwersje standardowe](standard-conversions.md) więcej informacji na temat jak jest wykonywane podwyższenia poziomu.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Jednoargumentowe operatory arytmetyczne](../c-language/unary-arithmetic-operators.md)