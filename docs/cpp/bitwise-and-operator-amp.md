---
title: Operator and:&amp;
description: Składnia operatora koniunkcji języka standardowego w języku C++ i użycie.
ms.date: 07/23/2020
f1_keywords:
- bitand_cpp
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: 7e78e4003a31ee59ebd974275df784b7a76e73ce
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229119"
---
# <a name="bitwise-and-operator-amp"></a>Operator and:&amp;

## <a name="syntax"></a>Składnia

> *wyrażenie* **`&`** *wyrażenie*

## <a name="remarks"></a>Uwagi

Operator koniunkcji bitowej ( **`&`** ) porównuje każdy bit pierwszego operandu z odpowiadającym mu bitem drugiego operandu. Jeśli obie bity są 1, odpowiedni bit wynikowy jest ustawiony na 1. W przeciwnym razie odpowiedni bit wynikowy jest ustawiony na 0.

Oba operandy operatora bitowego or muszą mieć typy całkowite. Zwykle konwersje arytmetyczne omówione w [konwersji standardowej](standard-conversions.md) są stosowane do operandów.

## <a name="operator-keyword-for-"></a>Słowo kluczowe operatora dla &

Język C++ określa **`bitand`** jako alternatywną pisownię **`&`** . W języku C alternatywna pisownia jest podawana jako makro w \<iso646.h> nagłówku. W języku C++ alternatywna pisownia jest słowem kluczowym; Użycie \<iso646.h> lub odpowiednik języka C++ \<ciso646> jest przestarzałe. W programie Microsoft C++ [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Opcja kompilatora or jest wymagana do włączenia alternatywnej pisowni.

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

[Wbudowane operatory, pierwszeństwo i łączność języka C++](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory bitowe języka C](../c-language/c-bitwise-operators.md)
