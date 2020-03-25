---
title: 'Operator przecinkowy: ,'
ms.date: 11/04/2016
f1_keywords:
- '%2C'
helpviewer_keywords:
- comma operator
ms.assetid: 38e0238e-19da-42ba-ae62-277bfdab6090
ms.openlocfilehash: 6ea2bd5c0e7653ba7f81531a5c39df2da41662a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189770"
---
# <a name="comma-operator-"></a>Operator przecinkowy: ,

Zezwala na grupowanie dwóch instrukcji, w których jest oczekiwany.

## <a name="syntax"></a>Składnia

```
expression , expression
```

## <a name="remarks"></a>Uwagi

Operator przecinek ma łączność od lewej do prawej. Dwa wyrażenia oddzielone przecinkami są szacowane od lewej do prawej. Lewy operand jest zawsze oceniany, a wszystkie efekty uboczne są kończone przed oceną prawego operandu.

Przecinki mogą być używane jako separatory w niektórych kontekstach, takich jak listy argumentów funkcji. Nie należy mylić użycia przecinka jako separatora przy użyciu jako operatora; te dwa zastosowania są całkowicie różne.

Rozważ wyrażenie `e1, e2`. Typ i wartość wyrażenia to typ i wartość *E2*; wynik oceny *E1* jest odrzucany. Wynik jest l-wartością, jeśli prawy operand jest l-wartością.

Gdzie przecinek jest zwykle używany jako separator (na przykład w rzeczywistych argumentach funkcji lub agregacji inicjatorów), operator przecinki i jego operandy muszą być ujęte w nawiasy. Na przykład:

```cpp
func_one( x, y + 2, z );
func_two( (x--, y + 2), z );
```

W wywołaniu funkcji do `func_one` powyżej, trzy argumenty, oddzielone przecinkami, są przenoszone: `x`, `y + 2`i `z`. W wywołaniu funkcji do `func_two`, nawiasy wymuszają, aby kompilator interpretował pierwszy przecinek jako operator oceny sekwencyjnej. To wywołanie funkcji przekazuje dwa argumenty do `func_two`. Pierwszy argument jest wynikiem operacji sekwencyjnej oceny `(x--, y + 2)`, która ma wartość i typ wyrażenia `y + 2`; drugi argument jest `z`.

## <a name="example"></a>Przykład

```cpp
// cpp_comma_operator.cpp
#include <stdio.h>
int main () {
   int i = 10, b = 20, c= 30;
   i = b, c;
   printf("%i\n", i);

   i = (b, c);
   printf("%i\n", i);
}
```

```Output
20
30
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami dwuargumentowymi](../cpp/expressions-with-binary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operator obliczania sekwencyjnego](../c-language/sequential-evaluation-operator.md)
