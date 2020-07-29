---
title: 'Operator logiczny OR:  &#124;&#124;'
description: Składnia operatora logicznego lub składniowego języka C++ standard oraz użycie.
ms.date: 07/23/2020
f1_keywords:
- '||'
- or_cpp
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
ms.openlocfilehash: 1845aef59f88d5dd044cefedd21cb618e1102e13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225998"
---
# <a name="logical-or-operator-124124"></a>Operator logiczny OR:  &#124;&#124;

## <a name="syntax"></a>Składnia

> *wyrażenie* **`||`** logiczne or *wyrażenie logiczne-and-Expression*

## <a name="remarks"></a>Uwagi

Operator logiczny OR ( **`||`** ) zwraca wartość logiczną, **`true`** Jeśli jeden lub oba operandy są **`true`** i zwraca **`false`** w przeciwnym razie. Operandy są niejawnie konwertowane na typ **`bool`** przed oceną, a wynik jest typu **`bool`** . Logiczny lub ma łączność od lewej do prawej.

Operandy operatora logicznego OR nie muszą mieć tego samego typu, ale muszą być typu Boolean, całkowitego lub wskaźnika. Operandy są zwykle wyrażeniami relacyjnymi lub równości.

Pierwszy operand jest obliczany całkowicie i wszystkie efekty uboczne są kończone przed kontynuowaniem obliczania wyrażenia logicznego OR.

Drugi operand jest oceniany tylko wtedy, gdy pierwszy operand szacuje się na **`false`** , ponieważ obliczenia nie są konieczne, gdy wyrażenie logiczne or ma wartość **`true`** . Jest ona znana jako Ocena *krótkoterminowa* .

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

W powyższym przykładzie, jeśli `x` jest równe `w` , `y` , lub `z` , drugi argument funkcji jest `printf` obliczany do **`true`** , który jest następnie podwyższany do liczby całkowitej, a wartość 1 jest drukowana. W przeciwnym razie zostanie wyznaczona **`false`** wartość 0. Gdy tylko jeden z warunków zostanie oszacowany **`true`** , szacowanie zostanie zatrzymane.

## <a name="operator-keyword-for-124124"></a>Słowo kluczowe operatora dla &#124;&#124;

Język C++ określa **`or`** jako alternatywną pisownię **`||`** . W języku C alternatywna pisownia jest podawana jako makro w \<iso646.h> nagłówku. W języku C++ alternatywna pisownia jest słowem kluczowym; Użycie \<iso646.h> lub odpowiednik języka C++ \<ciso646> jest przestarzałe. W programie Microsoft C++ [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Opcja kompilatora or jest wymagana do włączenia alternatywnej pisowni.

## <a name="example"></a>Przykład

```cpp
// expre_Logical_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate logical OR
#include <iostream>
using namespace std;
int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b || b > c yields "
         << (a < b || b > c) << endl
         << "The false expression "
         << "a > b || b > c yields "
         << (a > b || b > c) << endl;
}
```

## <a name="see-also"></a>Zobacz także

[Wbudowane operatory, pierwszeństwo i łączność języka C++](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory logiczne języka C](../c-language/c-logical-operators.md)
