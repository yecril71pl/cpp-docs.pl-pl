---
title: 'Operator wyłączny sumy bitowej OR: ^'
description: Wzorzec języka C++ lub Składnia operatora OR.
ms.date: 07/23/2020
f1_keywords:
- xor_cpp
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
ms.openlocfilehash: b76c3d84d9548a73084b254a4179d1f679c33626
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2020
ms.locfileid: "87521164"
---
# <a name="bitwise-exclusive-or-operator-"></a>Operator wyłączny sumy bitowej OR: ^

## <a name="syntax"></a>Składnia

> *wyrażenie* **`^`** *wyrażenie*

## <a name="remarks"></a>Uwagi

Operator wyłączny bitowego or ( **`^`** ) porównuje każdy bit pierwszego operandu z odpowiadającym mu bitem drugiego operandu. Jeśli bit w jednym z operandów ma wartość 0, a bit w drugim operandzie wynosi 1, odpowiedni bit wynikowy jest ustawiony na 1. W przeciwnym razie odpowiedni bit wynikowy jest ustawiony na 0.

Oba operandy operatora muszą mieć typy całkowite. Zwykle konwersje arytmetyczne omówione w [konwersji standardowej](standard-conversions.md) są stosowane do operandów.

## <a name="operator-keyword-for-"></a>Słowo kluczowe operatora dla ^

Język C++ określa **`xor`** jako alternatywną pisownię **`^`** . W języku C alternatywna pisownia jest podawana jako makro w \<iso646.h> nagłówku. W języku C++ alternatywna pisownia jest słowem kluczowym; Użycie \<iso646.h> lub odpowiednik języka C++ \<ciso646> jest przestarzałe. W programie Microsoft C++ [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Opcja kompilatora or jest wymagana do włączenia alternatywnej pisowni.


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

[Wbudowane operatory, pierwszeństwo i łączność języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
