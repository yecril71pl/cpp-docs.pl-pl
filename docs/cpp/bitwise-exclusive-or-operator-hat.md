---
title: 'Operator wyłączny sumy bitowej OR: ^'
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
ms.openlocfilehash: 9a44dc60a985729aae79ed0e2e48c44adace647b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190719"
---
# <a name="bitwise-exclusive-or-operator-"></a>Operator wyłączny sumy bitowej OR: ^

## <a name="syntax"></a>Składnia

```
expression ^ expression
```

## <a name="remarks"></a>Uwagi

Operator wyłączny bitowego or ( **^** ) porównuje każdy bit pierwszego operandu z odpowiadającym mu bitem drugiego operandu. Jeśli jeden bit ma wartość 0, a drugi bit to 1, odpowiedni bit wynikowy jest ustawiony na 1. W przeciwnym razie odpowiedni bit wynikowy jest ustawiony na 0.

Oba argumenty operacji w operatorze wykluczającym or muszą być typami całkowitymi. Zwykle konwersje arytmetyczne omówione w [konwersji standardowej](standard-conversions.md) są stosowane do operandów.

## <a name="operator-keyword-for-"></a>Słowo kluczowe operatora dla ^

Operator **XOR** jest odpowiednikiem tekstu **^** . Istnieją dwa sposoby uzyskania dostępu do operatora **XOR** w programach: Dołącz plik nagłówka `iso646.h`lub Kompiluj z opcją kompilatora [/za](../build/reference/za-ze-disable-language-extensions.md) (Wyłącz rozszerzenia językowe).

## <a name="example"></a>Przykład

```cpp
// expre_Bitwise_Exclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise exclusive OR
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xFFFF;      // pattern 1111 ...

   cout  << hex << ( a ^ b ) << endl;   // prints "aaaa" pattern 1010 ...
}
```

## <a name="see-also"></a>Zobacz też

[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
