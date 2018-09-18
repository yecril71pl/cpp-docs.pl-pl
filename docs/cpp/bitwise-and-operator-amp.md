---
title: 'Bitowy Operator AND: &amp; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bitand
dev_langs:
- C++
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8967861ab6ac4e6b6fafd11eea22e67de339ea8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111384"
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