---
title: 'Operator logiczny OR: || | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '||'
dev_langs:
- C++
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37a7591e185b1436bb3cd0f8b56a625f71bf8ed2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073652"
---
# <a name="logical-or-operator-"></a>Operator logiczny OR: ||

## <a name="syntax"></a>Składnia

> *lub wyrażenie logiczne* **||** *-i wyrażenie logiczne*

## <a name="remarks"></a>Uwagi

Operator logiczny OR (**||**) zwraca wartość logiczną PRAWDA, jeśli ma wartość TRUE lub obydwa operandy, a w przeciwnym razie zwraca wartość FALSE. Argumenty operacji są niejawnie konwertowane na typ **bool** przed oceny, a wynik jest typu **bool**. Operator logiczny lub ma łączność od lewej do prawej.

Argumenty operacji dla operatora logicznego OR nie muszą być tego samego typu, ale muszą być typu wartości całkowitej lub wskaźnika. Argumenty operacji są często relacyjnych lub wyrażeniach porównania.

Pierwszy operand jest obliczane całkowicie, wraz ze wszystkimi efektami ubocznymi odbywa się przed kontynuowaniem oceny wyrażenie logiczne OR.

Drugi operand jest oceniany, tylko wtedy, gdy pierwszy operand wartość false (0). Pozwala to wyeliminować niepotrzebnego oceny drugiego operandu, gdy wyrażenie logiczne OR ma wartość true.

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

W powyższym przykładzie Jeśli `x` jest równa albo `w`, `y`, lub `z`, drugi argument `printf` funkcja zwraca wartość true, a wartość 1, wydrukowaniu. W przeciwnym razie zwróci wartość false, a wartość 0, wydrukowaniu. Tak szybko, jak jeden z warunków jest spełniony, zakończenie oceny.

## <a name="operator-keyword-for-124124"></a>Operator — słowo kluczowe dla&#124;&#124;

**Lub** operator jest odpowiednikiem tekstu **||**. Istnieją dwa sposoby dostępu do **lub** operatora w programach: uwzględnić plik nagłówka \<iso646.h >, lub kompilowanie z [/Za](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora (Wyłącz rozszerzenia językowe).

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

[Operatory języka C++ wbudowane pierwszeństwo i łączność](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatory logiczne języka C](../c-language/c-logical-operators.md)