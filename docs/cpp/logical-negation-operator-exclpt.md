---
title: 'Operator logiczny negacji: !'
description: Składnia logicznego operatora negacji języka standardowego C++ i użycie.
ms.date: 07/23/2020
f1_keywords:
- '!'
helpviewer_keywords:
- '! operator'
- NOT operator
- logical negation
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
ms.openlocfilehash: fdd2e7a71b791375f898372d058a5eeb2afc59f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223684"
---
# <a name="logical-negation-operator-"></a>Operator logiczny negacji: !

## <a name="syntax"></a>Składnia

> **`!`***wyrażenie cast*

## <a name="remarks"></a>Uwagi

Operator logiczny negacji ( **`!`** ) odwraca znaczenie jego operandu. Argument operacji musi być typu arytmetycznego lub wskaźnika (lub wyrażenia, które ma wartość arytmetyczną lub typu wskaźnika). Operand jest niejawnie konwertowany na typ **`bool`** . Wynikiem jest **`true`** przekonwertowanie operandu **`false`** ; wynikiem jest to, **`false`** czy przekonwertowany operand to **`true`** . Wynik jest typu **`bool`** .

Wyrażenie `e` jednoargumentowe `!e` jest równoznaczne z wyrażeniem `(e == 0)` , z wyjątkiem przypadków, w których są wykorzystywane przeciążone operatory.

## <a name="operator-keyword-for-"></a>Słowo kluczowe operatora dla!

Język C++ określa **`not`** jako alternatywną pisownię **`!`** . W języku C alternatywna pisownia jest podawana jako makro w \<iso646.h> nagłówku. W języku C++ alternatywna pisownia jest słowem kluczowym; Użycie \<iso646.h> lub odpowiednik języka C++ \<ciso646> jest przestarzałe. W programie Microsoft C++ [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Opcja kompilatora or jest wymagana do włączenia alternatywnej pisowni.

## <a name="example"></a>Przykład

```cpp
// expre_Logical_NOT_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
    int i = 0;
    if (!i)
        cout << "i is zero" << endl;
}
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i łączność języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Jednoargumentowe operatory arytmetyczne](../c-language/unary-arithmetic-operators.md)<br/>
