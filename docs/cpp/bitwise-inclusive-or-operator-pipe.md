---
title: 'Operator włączny sumy bitowej OR: |'
ms.date: 06/14/2018
f1_keywords:
- '|'
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
ms.openlocfilehash: 0df3493930206d655c0d9bca8a2468151aa3c2c6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445511"
---
# <a name="bitwise-inclusive-or-operator-"></a>Operator włączny sumy bitowej OR: |

## <a name="syntax"></a>Składnia

> *wyrażenie1* **|** *wyrażenie2*

## <a name="remarks"></a>Uwagi

Operator koniunkcji bitowej ( **&#124;** ) porównuje każdy bit pierwszego operandu z odpowiadającym mu bitem drugiego operandu. Jeśli jeden z bitów to 1, odpowiedni bit wynikowy jest ustawiony na 1. W przeciwnym razie odpowiedni bit wynikowy jest ustawiony na 0.

Oba argumenty operacji dla operatora bitowego or, muszą być typami całkowitymi. Zwykle konwersje arytmetyczne omówione w [konwersji standardowej](standard-conversions.md) są stosowane do operandów.

## <a name="operator-keyword-for-124"></a>Słowo kluczowe operatora dla&#124;

Operator **BitOr** jest odpowiednikiem tekstu **&#124;** . Istnieją dwa sposoby uzyskania dostępu do operatora **BitOr** w programach: Dołącz plik nagłówka \<iso646. h > lub skompiluj z opcją kompilatora [/za](../build/reference/za-ze-disable-language-extensions.md) (Disable Language Extensions).

## <a name="example"></a>Przykład

```cpp
// expre_Bitwise_Inclusive_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise inclusive OR
#include <iostream>
using namespace std;

int main() {
   unsigned short a = 0x5555;      // pattern 0101 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...
}
```

## <a name="see-also"></a>Zobacz też

[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory bitowe języka C](../c-language/c-bitwise-operators.md)