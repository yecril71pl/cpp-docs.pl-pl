---
title: "Program przykładowy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: fc22ef82-9caa-425f-b201-2891bc123d1f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 976b3c21e24a8e1e6c99664b31d32f85985d7f55
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="example-program"></a>Program przykładowy
Następujący program źródłowy C składa się z dwóch plików źródłowych. To daje przegląd różnych deklaracji i możliwych definicji w programie C. Nowsze w tej sekcji opisano sposób zapisania tych deklaracji, definicje i inicjalizacji i sposobu używania słowa kluczowe języka C, takich jak **statycznych** i `extern`. Funkcja `printf` jest zadeklarowana w pliku nagłówka STDIO.H języka C  
  
 Założono, że funkcje `main` i `max` są w oddzielnych plikach i wykonywanie programu rozpoczyna się od funkcji `main`. Niejawne funkcje użytkownika są wykonywane przed `main`.  
  
```  
/*****************************************************************  
                    FILE1.C - main function  
*****************************************************************/  
  
#define ONE     1  
#define TWO     2  
#define THREE   3  
#include <stdio.h>  
  
int a = 1;                       // Defining declarations      
int b = 2;                       //  of external variables      
  
extern int max( int a, int b );  // Function prototype          
  
int main()                       // Function definition         
{                                //  for main function          
    int c;                       // Definitions for      
    int d;                       //  two uninitialized  
                                 //  local variables  
  
    extern int u;                // Referencing declaration     
                                 //  of external variable       
                                 //  defined elsewhere          
    static int v;                // Definition of variable      
                                 //  with continuous lifetime   
  
    int w = ONE, x = TWO, y = THREE;  
    int z = 0;  
  
    z = max( x, y );             // Executable statements      
    w = max( z, w );  
    printf_s( "%d %d\n", z, w );  
    return 0;  
}  
  
/****************************************************************  
            FILE2.C - definition of max function  
****************************************************************/  
  
int max( int a, int b )          // Note formal parameters are     
                                 //  included in function header   
{  
    if( a > b )  
        return( a );  
    else  
        return( b );  
}  
```  
  
 FILE1.C zawiera prototyp dla funkcji `max`. Tego rodzaju deklaracja jest czasami nazywana „deklaracją do przodu”, gdyż funkcja jest zadeklarowana przed użyciem. Definicja dla funkcji `main` obejmuje wywołania do `max`.  
  
 Wiersze rozpoczynające się od `#define` są dyrektywami preprocesora. Dyrektywy informują preprocesor, aby zastąpił identyfikatory `ONE`, `TWO`, i `THREE` odpowiednio numerami `1`, `2` i `3`, w całym FILE1.C. Jednakże dyrektywy nie dotyczą FILE2.C, które jest kompilowany oddzielnie, a następnie łączony z FILE1.C. Wiersz zaczynający się od `#include` informuje kompilator o dołączenie pliku STDIO.H, który zawiera prototyp dla funkcji `printf`. [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md) opisano szczegółowo w *odwołania preprocesora*.  
  
 FILE1.C używa deklaracji definiujących do inicjowania zmiennych globalnych `a` i `b`. Zmienne lokalne `c` i `d` są zadeklarowane, ale nie zainicjowane. Magazyn jest przydzielany dla wszystkich zmiennych. Zmienne statyczne i zewnętrzne `u` i `v`, są automatycznie inicjowane z wartością 0. Dlatego tylko `a`, `b`, `u` i `v` zawierają istotne wartości, gdy są deklarowane, gdyż są inicjowanie jawnie lub niejawnie. FILE2.C zawiera definicję funkcji dla `max`. Definicja spełnia wywołania do `max` w FILE1.C.  
  
 Okres istnienia i widoczności identyfikatorów, które zostały omówione w [okres istnienia, zakres, widoczność i połączenie](../c-language/lifetime-scope-visibility-and-linkage.md). Aby uzyskać więcej informacji na temat funkcji, zobacz [funkcji](../c-language/functions-c.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)