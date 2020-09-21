---
title: 'Operator wyłączny sumy bitowej OR: ^'
description: Wzorzec języka C++ lub Składnia operatora OR.
ms.date: 09/21/2020
f1_keywords:
- xor_cpp
- ^
helpviewer_keywords:
- operators [C++], bitwise
- exclusive OR operator
- XOR operator
- bitwise operators [C++], OR operator
- ^ operator
- OR operator [C++], bitwise exclusive
- operators [C++], logical
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
ms.openlocfilehash: 4823c245ffca7032347e37c0c25c2963407733a7
ms.sourcegitcommit: f656092eebbcb148ca4d3b7a6a8508eff8f7e85f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2020
ms.locfileid: "90836631"
---
# <a name="bitwise-exclusive-or-operator-"></a>Operator wyłączny sumy bitowej OR: ^

## <a name="syntax"></a>Składnia

> *wyrażenie* **`^`** *wyrażenie*

## <a name="remarks"></a>Uwagi

Operator wyłączny bitowego or ( **`^`** ) porównuje każdy bit pierwszego operandu z odpowiadającym mu bitem drugiego operandu. Jeśli bit w jednym z operandów ma wartość 0, a bit w drugim operandzie wynosi 1, odpowiedni bit wynikowy jest ustawiony na 1. W przeciwnym razie odpowiedni bit wynikowy jest ustawiony na 0.

Oba operandy operatora muszą mieć typy całkowite. Zwykle konwersje arytmetyczne omówione w [konwersji standardowej](standard-conversions.md) są stosowane do operandów.

Aby uzyskać więcej informacji na temat alternatywnego użycia **`^`** znaku w c++/CLI i c++/CX, zobacz [uchwyt do operatora obiektu (^) (c++/CLI i c++/CX)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md).

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

## <a name="see-also"></a>Zobacz też

[Wbudowane operatory, pierwszeństwo i łączność języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
