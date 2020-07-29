---
title: Operator logiczny i:&amp;&amp;
description: Składnia operatora logicznego i wzorca języka C++ standard oraz użycie.
ms.date: 07/23/2020
f1_keywords:
- '&&'
- and_cpp
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
ms.openlocfilehash: 431e76a2943c2373d6191f1fbe9f14c54cfaa6c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223697"
---
# <a name="logical-and-operator-ampamp"></a>Operator logiczny i:&amp;&amp;

## <a name="syntax"></a>Składnia

> *wyrażenie* **`&&`** *wyrażenie*

## <a name="remarks"></a>Uwagi

Operator logiczny AND ( **&&** ) zwraca, **`true`** Jeśli oba operandy są **`true`** i zwracają **`false`** w przeciwnym razie. Operandy są niejawnie konwertowane na typ **`bool`** przed oceną, a wynik jest typu **`bool`** . Koniunkcja logiczna i ma łączność od lewej do prawej.

Operandy operatora logicznego AND nie muszą mieć tego samego typu, ale muszą mieć typ Boolean, całkowity lub wskaźnik. Operandy są zwykle wyrażeniami relacyjnymi lub równości.

Pierwszy operand jest obliczany całkowicie i wszystkie efekty uboczne są kończone przed kontynuowaniem oceny logicznej i wyrażenia.

Drugi operand jest oceniany tylko wtedy, gdy pierwszy operand ocenia wartość **`true`** (nierówną zero). Ta ocena eliminuje konieczność oceny drugiego operandu, gdy wyrażenie logiczne AND ma wartość **`false`** . Możesz użyć tej oceny krótkiego obwodu, aby zapobiec dereferencji wskaźnika o wartości null, jak pokazano w następującym przykładzie:

```cpp
char *pch = 0;
// ...
(pch) && (*pch = 'a');
```

Jeśli `pch` ma wartość null (0), prawa strona wyrażenia nigdy nie jest szacowana. Ta ocena krótkiego obwodu sprawia, że przypisanie przez wskaźnik o wartości null nie jest możliwe.

## <a name="operator-keyword-for-"></a>Słowo kluczowe operatora dla &&

Język C++ określa **`and`** jako alternatywną pisownię **`&&`** . W języku C alternatywna pisownia jest podawana jako makro w \<iso646.h> nagłówku. W języku C++ alternatywna pisownia jest słowem kluczowym; Użycie \<iso646.h> lub odpowiednik języka C++ \<ciso646> jest przestarzałe. W programie Microsoft C++ [`/permissive-`](../build/reference/permissive-standards-conformance.md) [`/Za`](../build/reference/za-ze-disable-language-extensions.md) Opcja kompilatora or jest wymagana do włączenia alternatywnej pisowni.

## <a name="example"></a>Przykład

```cpp
// expre_Logical_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate logical AND
#include <iostream>

using namespace std;

int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b && b < c yields "
         << (a < b && b < c) << endl
         << "The false expression "
         << "a > b && b < c yields "
         << (a > b && b < c) << endl;
}
```

## <a name="see-also"></a>Zobacz także

[Wbudowane operatory, pierwszeństwo i łączność języka C++](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory logiczne języka C](../c-language/c-logical-operators.md)
