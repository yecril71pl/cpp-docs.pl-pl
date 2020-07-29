---
title: goto i Labeled — instrukcje (C)
ms.date: 11/04/2016
f1_keywords:
- goto
helpviewer_keywords:
- labeled statement
- statements, labeled
- goto keyword [C]
ms.assetid: 3d0473dc-4b18-4fcc-9616-31a38499d7d7
ms.openlocfilehash: d84aa6701ef030dc494f6a40a7223d6f9bcd5073
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199987"
---
# <a name="goto-and-labeled-statements-c"></a>goto i Labeled — instrukcje (C)

**`goto`** Instrukcja przekazuje formant do etykiety. Dana etykieta musi znajdować się w tej samej funkcji i może występować przed tylko jedną instrukcją w tej samej funkcji.

## <a name="syntax"></a>Składnia

*instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Etykieta — instrukcja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*skoku — instrukcja*

*skok-instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`goto`**  *Identyfikator*  **;**

*etykieta — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*  **:**  *instrukcja*

Etykieta instrukcji jest istotna tylko dla **`goto`** instrukcji; w dowolnym innym kontekście instrukcja oznaczona etykietą jest wykonywana bez względu na etykietę.

*Instrukcja skoku* musi znajdować się w tej samej funkcji i może wystąpić przed tylko jedną instrukcją w tej samej funkcji. Zestaw nazw *identyfikatorów* po **`goto`** ma własną przestrzeń nazw, więc nazwy nie zakłócają innych identyfikatorów. Nie można ponownie zadeklarować etykiet. Aby uzyskać więcej informacji, zobacz [spacje nazw](../c-language/name-spaces.md) .

Jest dobrym stylem programowania, aby użyć **`break`** **`continue`** instrukcji,, i **`return`** w preferencjach do **`goto`** zawsze wtedy, gdy jest to możliwe. Ponieważ **`break`** instrukcja kończy się tylko z jednego poziomu pętli, **`goto`** może być konieczne do wykończenia pętli z głęboko zagnieżdżonej pętli.

Ten przykład ilustruje **`goto`** instrukcję:

```c
// goto.c
#include <stdio.h>

int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 3; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 5 )
                goto stop;
        }
    }

    /* This message does not print: */
    printf_s( "Loop exited. i = %d\n", i );

    stop: printf_s( "Jumped to stop. i = %d\n", i );
}
```

W tym przykładzie **`goto`** instrukcja przekazuje formant do punktu oznaczonego etykietą, `stop` gdy `i` jest równa 5.

## <a name="see-also"></a>Zobacz także

[Instrukcje](../c-language/statements-c.md)
