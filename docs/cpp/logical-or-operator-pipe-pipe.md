---
title: 'Operator logiczny OR: ||'
ms.date: 06/14/2018
f1_keywords:
- '||'
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
ms.openlocfilehash: 94b2bc024dd7223ac7adacc72924f5ee289bab37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178083"
---
# <a name="logical-or-operator-"></a>Operator logiczny OR: ||

## <a name="syntax"></a>Składnia

> wyrażenie *logiczne-and-* Expression **||** *logiczne i wyrażenie*

## <a name="remarks"></a>Uwagi

Operator logiczny OR ( **||** ) zwraca wartość logiczną PRAWDA, jeśli jeden lub oba operandy mają wartość true i w przeciwnym razie zwraca wartość false. Operandy są niejawnie konwertowane na typ **bool** przed oszacowaniem, a wynik jest typu **bool**. Logiczny lub ma łączność od lewej do prawej.

Operandy operatora logicznego OR nie mogą być tego samego typu, ale muszą być typu całkowitego lub wskaźnika. Operandy są zwykle wyrażeniami relacyjnymi lub równości.

Pierwszy operand jest obliczany całkowicie i wszystkie efekty uboczne są kończone przed kontynuowaniem obliczania wyrażenia logicznego OR.

Drugi operand jest oceniany tylko wtedy, gdy pierwszy operand zwraca wartość false (0). Eliminuje to potrzebę niepotrzebnej oceny drugiego operandu, gdy wyrażenie logiczne OR ma wartość true.

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

W powyższym przykładzie, jeśli `x` jest równa `w`, `y`lub `z`, drugi argument funkcji `printf` zwróci wartość true, a wartość 1 jest drukowana. W przeciwnym razie zostanie wyznaczona wartość false i zostanie wydrukowany wynik 0. Gdy tylko jeden z warunków zwróci wartość true, ocena zostanie przerwana.

## <a name="operator-keyword-for-124124"></a>Słowo kluczowe operatora dla&#124;&#124;

Operator **or** jest odpowiednikiem tekstu **||** . Istnieją dwa sposoby uzyskania dostępu do operatora **or** w programach: Dołącz plik nagłówka \<iso646. h > lub skompiluj z opcją kompilatora [/za](../build/reference/za-ze-disable-language-extensions.md) (Disable Language Extensions).

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

## <a name="see-also"></a>Zobacz też

[C++Pierwszeństwo operatorów wbudowanych i łączność](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory logiczne języka C](../c-language/c-logical-operators.md)
