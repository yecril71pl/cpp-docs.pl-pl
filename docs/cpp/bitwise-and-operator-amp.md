---
title: 'Bitowy Operator AND: &amp;'
ms.date: 11/04/2016
f1_keywords:
- bitand
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: b7d0d73802a5af7ab71e980d73eaff5c5b3c4bb8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387711"
---
# <a name="bitwise-and-operator-amp"></a>Bitowy Operator AND: &amp;

## <a name="syntax"></a>Składnia

```
expression & expression
```

## <a name="remarks"></a>Uwagi

Wyrażenie może być inne i wyrażeń lub (podlegające ograniczenia typu wymienione poniżej) wyrażeń równości, wyrażenia relacyjnych, wyrażenia dodatku, wyrażenia mnożenia, wskaźnik do elementu członkowskiego wyrażeń wyrażenia cast jednoargumentowy wyrażenia przyrostków wyrażenia lub wyrażeń, podstawowej.

Bitowy operator AND (**&**) porównuje każdy bit pierwszego operandu na odpowiadający mu bit drugiego operandu. Jeśli oba bity są 1, odpowiadający mu bit wynik jest równa 1. W przeciwnym razie odnośny bit wynik jest równa 0.

Bitowy operator AND oba operandy muszą być typami całkowitymi. Popularne konwersje arytmetyczne omówione w [konwersje standardowe](standard-conversions.md), są stosowane do operandów.

## <a name="operator-keyword-for-"></a>Operator — słowo kluczowe dla &

**Bitand** operator jest odpowiednikiem tekstu **&**. Istnieją dwa sposoby dostępu do **bitand** operatora w programach: uwzględnić plik nagłówka `iso646.h`, lub kompilowanie z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).

## <a name="example"></a>Przykład

```cpp
// expre_Bitwise_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise AND
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0xFFFF;      // pattern 1111 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a & b ) << endl;   // prints "aaaa", pattern 1010 ...
}
```

## <a name="see-also"></a>Zobacz także

[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory bitowe języka C](../c-language/c-bitwise-operators.md)