---
title: Ostrzeżenie kompilatora (poziom 2) C4146
ms.date: 11/04/2016
f1_keywords:
- C4146
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
ms.openlocfilehash: b945853a3d32f91c821d6fa174371df39bf183b3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218159"
---
# <a name="compiler-warning-level-2-c4146"></a>Ostrzeżenie kompilatora (poziom 2) C4146

jednoargumentowy operator minus zastosowany do typu bez znaku; wynik nadal jest niepodpisany

Typy bez znaku mogą zawierać tylko wartości nieujemne, więc jednoargumentowe minus (Negacja) nie ma na ogół sensu w przypadku zastosowania do typu bez znaku. Oba operandy i wynik są nieujemne.

Praktycznie, dzieje się tak, gdy programista próbuje wyrazić minimalną wartość całkowitą, czyli-2147483648. Ta wartość nie może być zapisywana jako-2147483648, ponieważ wyrażenie jest przetwarzane na dwóch etapach:

1. Oceniana jest liczba 2147483648. Ponieważ jest większa niż maksymalna liczba całkowita 2147483647, typ 2147483648 nie jest liczbą [int](../../c-language/integer-types.md), ale **`unsigned int`** .

1. Jednoargumentowy znak minus jest stosowany do wartości z niepodpisanym wynikiem, który również ma wartość 2147483648.

Niepodpisany typ wyniku może spowodować nieoczekiwane zachowanie. Jeśli wynik jest używany w porównaniu, można użyć niepodpisanego porównania, na przykład gdy inny operand jest **`int`** . To wyjaśnia, dlaczego Przykładowy program drukuje tylko jeden wiersz.

Oczekiwany drugi wiersz, `1 is greater than the most negative int` ,,, nie jest drukowany, ponieważ `((unsigned int)1) > 2147483648` ma wartość false.

Możesz uniknąć C4146, korzystając z INT_MIN z wartości Limits. h, który ma typ **`signed int`** .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4146:

```cpp
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
