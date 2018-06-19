---
title: Dlaczego liczby zmiennoprzecinkowe mogą tracić dokładność | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb673f087d98f6c7acdd1e98b5649cc84a48d277
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376140"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>Dlaczego liczby zmiennoprzecinkowe mogą tracić dokładność
Zmiennoprzecinkowe wartości dziesiętnych zwykle nie mają dokładnie reprezentacja binarna. To jest efektem ubocznym jak procesor CPU reprezentuje przestawne punktu danych. Z tego powodu mogą wystąpić utratę dokładności i niektóre operacje zmiennoprzecinkowe może dać nieoczekiwane wyniki.  
  
 To zachowanie jest wynikiem jedną z następujących czynności:  
  
-   Reprezentacja binarna liczba dziesiętna może nie być dokładnie.  
  
-   Wystąpiła niezgodność typów między liczbami używane (np. mieszania zmiennoprzecinkowych i o podwójnej precyzji).  
  
 Aby rozwiązać problem, większość programistów, albo upewnij się, że wartość jest większa lub mniejsza niż to, co jest potrzebne, lub Pobierz i używać biblioteki Binary Coded Decimal (BCD), które będzie odpowiadać za utrzymanie dokładność.  
  
 Binarna reprezentacja wartości zmiennoprzecinkowych ma wpływ na dokładność obliczeń zmiennoprzecinkowych. Microsoft Visual C++ używa [format liczb zmiennoprzecinkowych IEEE](../../build/reference/ieee-floating-point-representation.md).  
  
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
 EPSILON, można użyć stałe flt_epsilon —, który jest zdefiniowany dla typu float jako 1.192092896e-07F, lub dbl_epsilon —, który jest zdefiniowany dla typu double jako 2.2204460492503131e-016. Należy uwzględnić float.h — te stałych. Te stałe są zdefiniowane jako najmniejszą liczbę dodatnią numeru x, na przykład x + 1.0 nie jest równa 1.0. Ponieważ jest to bardzo małej liczby, powinny zostać zdefiniowane przez użytkownika na uszkodzenia w obliczeniach obejmujących bardzo dużych liczb.  
  
## <a name="see-also"></a>Zobacz też  
 [Optymalizacja kodu](../../build/reference/optimizing-your-code.md)