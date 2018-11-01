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
ms.openlocfilehash: 07af1b507cf256b84ac2f0f2db4061790a23555a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659618"
---
# <a name="bitwise-exclusive-or-operator-"></a>Operator wyłączny sumy bitowej OR: ^

## <a name="syntax"></a>Składnia

```
expression ^ expression
```

## <a name="remarks"></a>Uwagi

Bitowy operator OR wyłączne (**^**) porównuje każdy bit pierwszy argument operacji na odpowiadający mu bit drugim argumentem. Jeśli jeden bit ma wartość 0, a inne bit ma wartość 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odnośny bit wynik jest równa 0.

Oba operandy bitowe wyłączny operator OR musi być typu całkowitoliczbowego. Popularne konwersje arytmetyczne omówione w [konwersje standardowe](standard-conversions.md) są stosowane do operandów.

## <a name="operator-keyword-for-"></a>Operator — słowo kluczowe dla ^

**Xor** operator jest odpowiednikiem tekstu **^**. Istnieją dwa sposoby dostępu do **xor** operatora w programach: uwzględnić plik nagłówka `iso646.h`, lub kompilowanie z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).

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

## <a name="see-also"></a>Zobacz także

[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)