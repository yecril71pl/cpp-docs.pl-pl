---
title: 'Operator koniunkcji bitowej: &amp;'
ms.date: 11/04/2016
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: ba17c9a633b7b18cad2881dfef90fde7c2074319
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446138"
---
# <a name="bitwise-and-operator-amp"></a>Operator koniunkcji bitowej: &amp;

## <a name="syntax"></a>Składnia

```
expression & expression
```

## <a name="remarks"></a>Uwagi

Wyrażenia mogą być inne i-Expressions lub (zgodnie z ograniczeniami typu wymienionymi poniżej) wyrażenia równości, wyrażenia relacyjne, wyrażenia dodatków, wyrażenia mnożenia, wskaźniki do elementów członkowskich, wyrażenia rzutowania, jednoargumentowe wyrażenia, wyrażenia przyrostkowe lub wyrażenia podstawowe.

Operator koniunkcji bitowej ( **&** ) porównuje każdy bit pierwszego operandu z odpowiednim bitem drugiego operandu. Jeśli obie bity są 1, odpowiedni bit wynikowy jest ustawiony na 1. W przeciwnym razie odpowiedni bit wynikowy jest ustawiony na 0.

Oba operandy operatora bitowego and muszą być typami całkowitymi. Zwykle konwersje arytmetyczne omówione w [konwersji standardowej](standard-conversions.md)są stosowane do operandów.

## <a name="operator-keyword-for-"></a>Słowo kluczowe operatora dla &

Operator **BitAnd** jest odpowiednikiem tekstu **&** . Istnieją dwa sposoby uzyskania dostępu do operatora **BitAnd** w programach: Dołącz plik nagłówka `iso646.h`lub skompiluj z opcją [/za](../build/reference/za-ze-disable-language-extensions.md) (Wyłącz rozszerzenia językowe).

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

## <a name="see-also"></a>Zobacz też

[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory bitowe języka C](../c-language/c-bitwise-operators.md)