---
title: 'Operator dopełnienia jednostkowego: ~'
description: Składnia operatora uzupełniania języka C++ w wersji Standard i użycie.
ms.date: 07/23/2020
f1_keywords:
- "~"
- compl_cpp
helpviewer_keywords:
- tilde (~) one's complement operator
- one's complement operator
- bitwise-complement operator
- compl operator
- ~ operator [C++], syntax
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
ms.openlocfilehash: 89c67855cd67df2af315cea941b487e7462889b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227247"
---
# <a name="ones-complement-operator-"></a>Operator dopełnienia jednostkowego: ~

## <a name="syntax"></a>Składnia

```cpp
~ cast-expression
```

## <a name="remarks"></a>Uwagi

Operator dopełnienia ( **`~`** ), czasami nazywany operatorem dopełnienia *bitowego* , daje bitową część tego operandu. Oznacza to, że każdy bit, który jest 1 w operandzie, ma wartość 0 w wyniku. Z kolei każdy bit, który jest równy 0 w operandzie, ma wartość 1 w wyniku. Operand do operatora dopełnienia musi być typem całkowitym.

## <a name="operator-keyword-for-"></a>Słowo kluczowe operatora dla ~

Język C++ określa **`compl`** jako alternatywną pisownię **`~`** . W języku C alternatywna pisownia jest podawana jako makro w \<iso646.h> nagłówku. W języku C++ alternatywna pisownia jest słowem kluczowym; Użycie \<iso646.h> lub odpowiednik języka C++ \<ciso646> jest przestarzałe. W programie Microsoft C++ [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Opcja kompilatora or jest wymagana do włączenia alternatywnej pisowni.

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

Promocja typu całkowitego jest wykonywana w przypadku całkowitych argumentów operacji. Typ, do którego zostanie podwyższony argument, to wynikowy typ. Aby uzyskać więcej informacji na temat promocji całkowitej, zobacz [standardowe konwersje](standard-conversions.md).

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](expressions-with-unary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i łączność języka C++](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Jednoargumentowe operatory arytmetyczne](../c-language/unary-arithmetic-operators.md)
