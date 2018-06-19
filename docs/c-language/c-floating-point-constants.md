---
title: Stałe zmiennoprzecinkowe języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- types [C], constants
- floating-point numbers, floating-point constants
- constants, floating-point
- floating-point constants
- floating-point constants, about floating-point constants
- double data type, floating-point constants
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3608e40db2aa3eb0c49942de278c1d428e26689f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385100"
---
# <a name="c-floating-point-constants"></a>Stałe zmiennoprzecinkowe języka C
"Stałej zmiennoprzecinkowej" jest liczbą dziesiętną, reprezentujący podpisem liczba rzeczywista. Reprezentacja podpisem liczba rzeczywista zawiera część całkowitą część ułamkowa i wykładnik. Stałe zmiennoprzecinkowe umożliwia reprezentują wartości zmiennoprzecinkowych, których nie można zmienić.  
  
## <a name="syntax"></a>Składnia  
 *Floating point stała*:  
 &nbsp;&nbsp; *wykładnik części ułamkowych stała*<sub>opt</sub> *zmiennoprzecinkową sufiks*<sub>opcjonalnych</sub>  
 &nbsp;&nbsp; *wykładnik części sekwencji cyfr zmiennoprzecinkową sufiks*<sub>opcjonalnych</sub>  
  
 *Stała ułamkowych*:  
 &nbsp;&nbsp; *cyfra sekwencji*<sub>opt</sub> **.** *cyfra sekwencji*  
 &nbsp;&nbsp; *cyfra sekwencji***.**   
  
 *wykładnik części*:  
 &nbsp;&nbsp; **e***znak*<sub>opt</sub> *sekwencji cyfr*   
 &nbsp;&nbsp; **E***znak*<sub>opt</sub> *sekwencji cyfr*   
  
 *znak* : jeden z  
 &nbsp;&nbsp; **+ -**  
  
 *cyfra sekwencji*:  
 &nbsp;&nbsp; *Cyfra*  
 &nbsp;&nbsp; *cyfra sekwencji cyfr*  
  
 *przestawne sufiks* : jeden z  
 &nbsp;&nbsp; **f, g F L**  
  
 Można pominąć cyfr przed separatorem dziesiętnym (część całkowitą wartość) albo cyfry po przecinku (część ułamkowa), ale nie obie. Możesz pozostawić limit dziesiętnego tylko wtedy, gdy obejmują wykładnik. Żadne znaki odstępu można oddzielić cyfr lub znaków stałej.  
  
 Poniższe przykłady przedstawiają niektóre rodzaje wyrażeń i stałe zmiennoprzecinkowe:  
  
```  
15.75  
1.575E1   /* = 15.75   */  
1575e-2   /* = 15.75   */  
-2.5e-3   /* = -0.0025 */  
25E-4     /* =  0.0025 */  
```  
  
 Stałe zmiennoprzecinkowe są dodatnie, chyba że są poprzedzone znakiem minus (**-**). W takim przypadku znak minus jest traktowany jako Jednoargumentowy operator negacji arytmetyczne. Stałe zmiennoprzecinkowe ma typ `float`, `double`, lub `long double`.  
  
 Stała zmiennoprzecinkowa bez **f**, **F**, **l**, lub **L** sufiks ma typ `double`. Jeśli litera **f** lub **F** jest sufiks stałej ma typ `float`. Jeśli sufiks litera **l** lub **L**, ma typ `long double`. Na przykład:  
  
```  
100L  /* Has type long double  */  
100F  /* Has type float        */  
```  
  
 Należy pamiętać, że kompilator Microsoft C wewnętrznie reprezentuje `long double` taki sam jak typ `double`. Zobacz [magazyn typów podstawowych](../c-language/storage-of-basic-types.md) informacji o typie `double`, `float`, i `long double`.  
  
 Część całkowitą wartość stałej zmiennoprzecinkowej, można pominąć, jak pokazano w poniższych przykładach. Liczba.75 może być wyrażona na wiele sposobów, łącznie z następujących czynności:  
  
```  
.0075e2  
0.075e1  
.075e1  
75e-2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe języka C](../c-language/c-constants.md)