---
title: goto i Labeled Statements (C) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: goto
dev_langs: C++
helpviewer_keywords:
- labeled statement
- statements, labeled
- goto keyword [C]
ms.assetid: 3d0473dc-4b18-4fcc-9616-31a38499d7d7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea0543a13d16850be4259d2d93f763dd0edcbda3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="goto-and-labeled-statements-c"></a>goto i Labeled — instrukcje (C)
`goto` Instrukcji przenosi formantu etykiety. Etykieta danego musi znajdować się w tej samej funkcji i mogą występować przed tylko jednej instrukcji w tej samej funkcji.  
  
## <a name="syntax"></a>Składnia  
 *Instrukcja*:  
 *z etykietą instrukcji*  
  
 *skok — instrukcja*  
  
 *Instrukcja skok*:  
 **Przejdź do***identyfikator***;**   
  
 *z etykietą instrukcji*:  
 *Identyfikator***:***— instrukcja*   
  
 Etykieta instrukcji jest znaczący tylko `goto` instrukcję w dowolnym kontekście labeled — instrukcja jest wykonywane niezależnie etykiety.  
  
 A *instrukcji skok* musi znajdować się w tej samej funkcji i mogą występować przed tylko jednej instrukcji w tej samej funkcji. Zbiór *identyfikator* następujące nazwy `goto` ma przestrzeni nazw, dlatego nazwy nie zakłóca innych identyfikatorów. Nie można ponownie zadeklarować etykiety. Zobacz [przestrzeniach nazw](../c-language/name-spaces.md) Aby uzyskać więcej informacji.  
  
 Zaleca programowania stylu **podziału**, **kontynuować**, i `return` instrukcji preference do `goto` zawsze, gdy jest to możliwe. Ponieważ **podziału** instrukcji zamknie tylko jeden poziom w pętli `goto` może być konieczne wyjścia z pętli w pętli głęboko zagnieżdżone.  
  
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
  
 W tym przykładzie `goto` instrukcji przekazuje sterowanie do punktu z etykietą `stop` podczas `i` jest równe 5.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje](../c-language/statements-c.md)