---
title: Dlaczego liczby zmiennoprzecinkowe mogą tracić dokładność
ms.date: 11/04/2016
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
ms.openlocfilehash: 6e6f758e7a683a28189123b03252223476ac732a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442669"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>Dlaczego liczby zmiennoprzecinkowe mogą tracić dokładność

Zmiennoprzecinkowe wartości dziesiętnej zwykle nie mają dokładnie reprezentacja binarna. To jest efektem jak procesor CPU reprezentuje zmiennoprzecinkową punktu danych. Z tego powodu może wystąpić pewną utratą dokładności i niektórych operacji zmiennoprzecinkowych może powodować nieoczekiwane rezultaty.

To zachowanie jest wynik jednego z następujących czynności:

- Reprezentacja binarna liczba dziesiętna, która może nie być dokładna.

- Wystąpiła niezgodność typu między liczbami używana (na przykład. mieszanie zmiennoprzecinkowe i podwójne).

Aby rozwiązać problem, większość programistów, albo upewnij się, że wartość jest większa lub mniejsza niż co jest potrzebne, lub pobrać i użyć biblioteki Binary Coded Decimal (BCD), która będzie utrzymywać dokładność.

Binarna reprezentacja wartości zmiennoprzecinkowych ma wpływ na dokładność wykonywania obliczeń zmiennopozycyjnych. Microsoft Visual C++ używa [formatu zmiennoprzecinkowego IEEE](../../build/reference/ieee-floating-point-representation.md).

## <a name="example"></a>Przykład

```
// Floating-point_number_precision.c
// Compile options needed: none. Value of c is printed with a decimal
// point precision of 10 and 6 (printf rounded value by default) to
// show the difference
#include <stdio.h>

#define EPSILON 0.0001   // Define your own tolerance
#define FLOAT_EQ(x,v) (((v - EPSILON) < x) && (x <( v + EPSILON)))

int main() {
   float a, b, c;

   a = 1.345f;
   b = 1.123f;
   c = a + b;
   // if (FLOAT_EQ(c, 2.468)) // Remove comment for correct result
   if (c == 2.468)            // Comment this line for correct result
      printf_s("They are equal.\n");
   else
      printf_s("They are not equal! The value of c is %13.10f "
                "or %f",c,c);
}
```

```Output
They are not equal! The value of c is  2.4679999352 or 2.468000
```

## <a name="comments"></a>Komentarze

EPSILON, można użyć stałe FLT_EPSILON, która jest zdefiniowana float jako 1.192092896e-07F, lub DBL_EPSILON, która jest zdefiniowana dla podwójnej precyzji jako 2.2204460492503131e-016. Konieczne jest uwzględnienie float.h dla tych stałych. Te stałe są zdefiniowane jako najmniejsza dodatnia liczba x, na przykład x + 1.0 nie jest równa 1.0. Ponieważ jest to bardzo małej liczby, powinny zostać zdefiniowane przez użytkownika na uszkodzenia w obliczeniach obejmujących bardzo dużych liczb.

## <a name="see-also"></a>Zobacz też

[Optymalizacja kodu](../../build/reference/optimizing-your-code.md)