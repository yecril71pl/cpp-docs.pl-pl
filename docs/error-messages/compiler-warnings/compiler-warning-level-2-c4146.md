---
title: Kompilator ostrzeżenie (poziom 2) C4146
ms.date: 11/04/2016
f1_keywords:
- C4146
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
ms.openlocfilehash: 8b3090f1bc3a64752ede4dab2b1e1b5cd800057d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555574"
---
# <a name="compiler-warning-level-2-c4146"></a>Kompilator ostrzeżenie (poziom 2) C4146

Jednoargumentowy minus operator zastosowany do typu unsigned, wynik nadal unsigned

Typy bez znaku może zawierać wartości tylko nieujemnej wartości, więc jednoargumentowego znaku minusa (negacja) nie ma zazwyczaj sensu w przypadku zastosowania do typ bez znaku. Wynik i argument są nieujemnej wartości.

W praktyce dzieje się tak podczas programistę do wyrażenia wartości minimalnej liczbie całkowitej, która jest -2147483648. Nie można zapisać tej wartości jako -2147483648, ponieważ wyrażenie jest przetwarzany w dwóch etapach:

1. Liczba 2147483648 jest oceniany. Ponieważ jest większa niż wartość maksymalna liczba całkowita 2147483647, nie jest typu 2147483648 [int](../../c-language/integer-types.md), ale `unsigned int`.

1. Minus jednoargumentowy jest stosowany do wynik bez znaku, który również ma miejsce 2147483648 wartością.

Bez znaku typu wyniku, może spowodować nieoczekiwane zachowanie. Jeśli zostanie użyty wynik porównania, a następnie niepodpisane porównania mogą być używane, na przykład, gdy jest to drugi operand `int`. To wyjaśnia, dlaczego poniższy program przykład drukuje tylko jeden wiersz.

Oczekiwano drugi wiersz `1 is greater than the most negative int`, nie jest drukowany, ponieważ `((unsigned int)1) > 2147483648` ma wartość false.

Możesz uniknąć C4146 przy użyciu INT_MIN z limits.h, która ma typ **podpisany int**.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4146:

```
// C4146.cpp
// compile with: /W2
#include <stdio.h>

void check(int i)
{
    if (i > -2147483648)   // C4146
        printf_s("%d is greater than the most negative int\n", i);
}

int main()
{
    check(-100);
    check(1);
}
```