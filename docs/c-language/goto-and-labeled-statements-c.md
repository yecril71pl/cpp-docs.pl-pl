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
ms.openlocfilehash: b23e7e6310ba4ed968e2eac8e6d07d81ee4e79ba
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151952"
---
# <a name="goto-and-labeled-statements-c"></a>goto i Labeled — instrukcje (C)

`goto` Instrukcji przekazuje sterowanie do etykiety. Etykieta danego musi znajdować się w tej samej funkcji i może następować przed elementem tylko jednej instrukcji w tej samej funkcji.

## <a name="syntax"></a>Składnia

*Instrukcja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*labeled-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Instrukcja skoku*

*Instrukcja skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Przejdź do***identyfikator***;**

*labeled-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator***:***— instrukcja*

Etykieta instrukcji jest istotny tylko `goto` instrukcję w dowolnym kontekście instrukcji oznaczonej etykietą jest wykonywane, bez względu na etykietę.

A *instrukcja skoku* musi znajdować się w tej samej funkcji i może następować przed elementem tylko jednej instrukcji w tej samej funkcji. Zbiór *identyfikator* następujące nazwy `goto` ma swój własny obszar nazw, więc nazwy kolidują z innymi identyfikatorami. Nie można ponownie zadeklarować etykiety. Zobacz [przestrzenie nazw](../c-language/name-spaces.md) Aby uzyskać więcej informacji.

Jest dobrą programowania stylu **podziału**, **nadal**, i `return` instrukcję preference do `goto` zawsze, gdy jest to możliwe. Ponieważ **podziału** instrukcja kończy się tylko z poziomu pętli, `goto` może być konieczne wyjścia z pętli w pętli głęboko zagnieżdżonych.

W tym przykładzie przedstawiono `goto` instrukcji:

```
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

W tym przykładzie `goto` instrukcji przekazuje sterowanie do punktu z etykietą `stop` podczas `i` jest równa 5.

## <a name="see-also"></a>Zobacz także

[Instrukcje](../c-language/statements-c.md)
