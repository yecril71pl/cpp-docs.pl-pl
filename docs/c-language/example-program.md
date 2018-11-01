---
title: Program przykładowy
ms.date: 11/04/2016
ms.assetid: fc22ef82-9caa-425f-b201-2891bc123d1f
ms.openlocfilehash: 31e8f822462dad7b3935548c9c25e7334a82b377
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608626"
---
# <a name="example-program"></a>Program przykładowy

Następujący program źródłowy C składa się z dwóch plików źródłowych. To daje przegląd różnych deklaracji i możliwych definicji w programie C. Nowsze rozdziały niniejszej książki opisują, jak napisać te deklaracje, definicje i inicjalizacje oraz jak używać słów kluczowych C takich jak **statyczne** i `extern`. Funkcja `printf` jest zadeklarowana w pliku nagłówkowym STDIO.H języka C.

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

Wiersze rozpoczynające się od `#define` są dyrektywami preprocesora. Dyrektywy informują preprocesor, aby zastąpił identyfikatory `ONE`, `TWO`, i `THREE` odpowiednio numerami `1`, `2` i `3`, w całym FILE1.C. Jednakże dyrektywy nie dotyczą FILE2.C, które jest kompilowany oddzielnie, a następnie łączony z FILE1.C. Wiersz zaczynający się od `#include` informuje kompilator o dołączenie pliku STDIO.H, który zawiera prototyp dla funkcji `printf`. [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md) są wyjaśnione w *Preprocessor Reference*.

FILE1.C używa deklaracji definiujących do inicjowania zmiennych globalnych `a` i `b`. Zmienne lokalne `c` i `d` są zadeklarowane, ale nie zainicjowane. Magazyn jest przydzielany dla wszystkich zmiennych. Zmienne statyczne i zewnętrzne `u` i `v`, są automatycznie inicjowane z wartością 0. Dlatego tylko `a`, `b`, `u` i `v` zawierają istotne wartości, gdy są deklarowane, gdyż są inicjowanie jawnie lub niejawnie. FILE2.C zawiera definicję funkcji dla `max`. Definicja spełnia wywołania do `max` w FILE1.C.

Okres istnienia i widoczność identyfikatorów omówiono w [okres istnienia, zakres, widoczność i powiązania](../c-language/lifetime-scope-visibility-and-linkage.md). Aby uzyskać więcej informacji na temat funkcji, zobacz [funkcji](../c-language/functions-c.md).

## <a name="see-also"></a>Zobacz też

[Pliki źródłowe i programy źródłowe](../c-language/source-files-and-source-programs.md)