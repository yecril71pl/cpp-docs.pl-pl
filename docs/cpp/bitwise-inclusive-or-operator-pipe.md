---
title: 'Operator włączny bitowego or: &#124;'
description: Składnia operatora bitowego lub składniowego standardowego języka C++ oraz użycie.
ms.date: 07/23/2020
f1_keywords:
- '|'
- bitor_cpp
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
ms.openlocfilehash: 76f80c2101b3acfac71dc4d8ad1be4a999f69aa5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229093"
---
# <a name="bitwise-inclusive-or-operator-124"></a>Operator włączny bitowego or: &#124;

## <a name="syntax"></a>Składnia

> *wyrażenie1* **`|`** *wyrażenie2*

## <a name="remarks"></a>Uwagi

Operator koniunkcji bitowej ( **`|`** ) porównuje każdy bit pierwszego operandu z odpowiadającym mu bitem drugiego operandu. Jeśli jeden z bitów to 1, odpowiedni bit wynikowy jest ustawiony na 1. W przeciwnym razie odpowiedni bit wynikowy jest ustawiony na 0.

Oba operandy operatora muszą mieć typy całkowite. Zwykle konwersje arytmetyczne omówione w [konwersji standardowej](standard-conversions.md) są stosowane do operandów.

## <a name="operator-keyword-for-124"></a>Słowo kluczowe operatora dla &#124;

Język C++ określa **`bitor`** jako alternatywną pisownię **`|`** . W języku C alternatywna pisownia jest podawana jako makro w \<iso646.h> nagłówku. W języku C++ alternatywna pisownia jest słowem kluczowym; Użycie \<iso646.h> lub odpowiednik języka C++ \<ciso646> jest przestarzałe. W programie Microsoft C++ [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Opcja kompilatora or jest wymagana do włączenia alternatywnej pisowni.

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

[Wbudowane operatory, pierwszeństwo i łączność języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory bitowe języka C](../c-language/c-bitwise-operators.md)
