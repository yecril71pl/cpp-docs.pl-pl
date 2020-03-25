---
title: 'Operator logiczny i: &amp;&amp;'
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
ms.openlocfilehash: b21d91009c455b67af6fae88fceafeeaf8043301
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179435"
---
# <a name="logical-and-operator-ampamp"></a>Operator logiczny i: &amp;&amp;

## <a name="syntax"></a>Składnia

```
expression && expression
```

## <a name="remarks"></a>Uwagi

Operator logiczny AND ( **&&** ) zwraca wartość logiczną PRAWDA, jeśli oba operandy mają wartość true i w przeciwnym razie zwraca wartość false. Operandy są niejawnie konwertowane na typ **bool** przed oszacowaniem, a wynik jest typu **bool**. Koniunkcja logiczna i ma łączność od lewej do prawej.

Operandy operatora logicznego AND nie muszą być tego samego typu, ale muszą być typu całkowitego lub wskaźnika. Operandy są zwykle wyrażeniami relacyjnymi lub równości.

Pierwszy operand jest obliczany całkowicie i wszystkie efekty uboczne są kończone przed kontynuowaniem oceny logicznej i wyrażenia.

Drugi operand jest oceniany tylko wtedy, gdy pierwszy operand zwraca wartość true (niezerową). Ta ocena eliminuje konieczność oceny drugiego operandu, gdy wyrażenie logiczne AND ma wartość false. Możesz użyć tej oceny krótkiego obwodu, aby zapobiec dereferencji wskaźnika o wartości null, jak pokazano w następującym przykładzie:

```cpp
char *pch = 0;
...
(pch) && (*pch = 'a');
```

Jeśli `pch` ma wartość null (0), prawa strona wyrażenia nigdy nie jest szacowana. W związku z tym przypisanie przez wskaźnik o wartości null jest niemożliwe.

## <a name="operator-keyword-for-"></a>Słowo kluczowe operatora dla & &

Operator **i** jest odpowiednikiem tekstu **&&** . Istnieją dwa sposoby uzyskania dostępu do operatora **i** w programach: Dołącz plik nagłówka `iso646.h`lub skompiluj przy użyciu opcji kompilatora [/za](../build/reference/za-ze-disable-language-extensions.md) (Wyłącz rozszerzenia językowe).

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

## <a name="see-also"></a>Zobacz też

[C++Pierwszeństwo operatorów wbudowanych i łączność](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory logiczne języka C](../c-language/c-logical-operators.md)
