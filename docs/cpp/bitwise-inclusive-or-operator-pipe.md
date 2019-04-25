---
title: 'Bitowe or włączny operator OR: |'
ms.date: 06/14/2018
f1_keywords:
- bitor
- '|'
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
ms.openlocfilehash: 848bf3b2ec61084b59ab5b1ee6807f6066a4675e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184296"
---
# <a name="bitwise-inclusive-or-operator-"></a>Bitowe or włączny operator OR: |

## <a name="syntax"></a>Składnia

> *expression1* **|** *expression2*

## <a name="remarks"></a>Uwagi

Bitowe włączny operator OR (**&#124;**) porównuje każdy bit pierwszy argument operacji na odpowiadający mu bit drugim argumentem. Jeśli bit albo ma wartość 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odnośny bit wynik jest równa 0.

Oba operandy bitowe włączny operator OR musi być typu całkowitoliczbowego. Popularne konwersje arytmetyczne omówione w [konwersje standardowe](standard-conversions.md) są stosowane do operandów.

## <a name="operator-keyword-for-124"></a>Operator keyword for &#124;

**Bitor** operator jest odpowiednikiem tekstu **&#124;**. Istnieją dwa sposoby dostępu do **bitor** operatora w programach: uwzględnić plik nagłówka \<iso646.h >, lub kompilowanie z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).

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

## <a name="see-also"></a>Zobacz także

[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory bitowe języka C](../c-language/c-bitwise-operators.md)