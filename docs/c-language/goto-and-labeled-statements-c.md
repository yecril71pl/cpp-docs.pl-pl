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
ms.openlocfilehash: b5e0d602332c87510b1fe5f59db3e497b88f0acb
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299120"
---
# <a name="goto-and-labeled-statements-c"></a>goto i Labeled — instrukcje (C)

Instrukcja `goto` przenosi formant do etykiety. Dana etykieta musi znajdować się w tej samej funkcji i może występować przed tylko jedną instrukcją w tej samej funkcji.

## <a name="syntax"></a>Składnia

*instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*labeled-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*skoku-instrukcja*

*skok-instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przejdź do** *identyfikator* **;**

*etykieta — instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator* **:** *— instrukcja*

Etykieta instrukcji jest istotna tylko dla instrukcji `goto`; w każdym innym kontekście wyrażenie z etykietą jest wykonywane bez względu na etykietę.

*Instrukcja skoku* musi znajdować się w tej samej funkcji i może wystąpić przed tylko jedną instrukcją w tej samej funkcji. Zestaw nazw *identyfikatorów* po `goto` ma własną przestrzeń nazw, więc nazwy nie zakłócają innych identyfikatorów. Nie można ponownie zadeklarować etykiet. Aby uzyskać więcej informacji, zobacz [spacje nazw](../c-language/name-spaces.md) .

Jest dobrym stylem programowania, aby użyć instrukcji **Break**, **Continue**i `return` w preferencjach, aby `goto`, gdy jest to możliwe. Ponieważ instrukcja **Break** jest zamykana tylko z jednego poziomu pętli, `goto` może być konieczne do wykończenia pętli z głęboko zagnieżdżonej pętli.

Ten przykład ilustruje instrukcję `goto`:

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

W tym przykładzie instrukcja `goto` przenosi formant do punktu oznaczonego etykietą `stop`, gdy `i` jest równa 5.

## <a name="see-also"></a>Zobacz także

[Instrukcje](../c-language/statements-c.md)
