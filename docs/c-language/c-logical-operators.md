---
title: Operatory logiczne języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- logical operators, expression sequence points
- logical operators, C
- logical AND operator
- '|| operator'
- operators [C], logical
- short-circuit evaluation
- '&& operator'
- logical OR operator
ms.assetid: c0a4e766-ad56-4300-bf76-b28dc0e19b43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f92adbeab4175178be8f41a09c4455d8a581131
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="c-logical-operators"></a>Operatory logiczne języka C
Operatory logiczne wykonania logicznej- i (**&&**) i operatora logicznego OR ( `||` ) operacji.  
  
 **Składnia**  
  
 *i wyrażenie logiczne*:  
 *wraz z wartościami granicznymi wyrażenie OR*  
  
 *i wyrażenie logiczne***&&***włącznie wyrażenie OR*   
  
 *wyrażenia logicznego lub*:  
 *i wyrażenie logiczne*  
  
 *wyrażenia logicznego lub***&#124;&#124;***-i wyrażenie logiczne*   
  
 Operatory logiczne nie wykonuj popularne konwersje arytmetyczne. Zamiast tego umożliwiają podawanie wartości każdy argument pod względem jego odpowiednik na 0. Wynik operacji logicznej jest równa 0 lub 1. Typ wyniku jest `int`.  
  
 Poniżej opisano operatory logiczne języka C:  
  
|Operator|Opis|  
|--------------|-----------------|  
|**&&**|Logiczny- i operatora daje wartość 1, jeśli oba argumenty mieć niezerowe wartości. Jeśli którykolwiek argument operacji jest równa 0, wynikiem jest wartość 0. Jeśli pierwszy argument operacji logicznych- i operacji jest równa 0, drugi argument nie jest obliczane.|  
|`&#124;&#124;`|Operator logiczny OR wykonuje operację włącznie lub argumentów. Wynik jest 0, jeśli oba argumenty mają wartości 0. Jeśli którykolwiek argument operacji ma wartość różną od zera, wynikiem jest 1. Drugi argument nie jest oceniany, jeśli pierwszy argument operacji operatora logicznego OR ma wartość różną od zera.|  
  
 Argumenty operacji logicznych- a i wyrażeń logicznych lub są oceniane od lewej do prawej. Drugi argument nie jest oceniany, jeśli wartość pierwszy argument operacji jest wystarczające, aby ustalić wyniku operacji. Jest to nazywane "ocena zwarcia." Brak punktu sekwencji po pierwszym argumentem. Zobacz [punkty sekwencji](../c-language/c-sequence-points.md) Aby uzyskać więcej informacji.  
  
## <a name="examples"></a>Przykłady  
 Poniższe przykłady przedstawiają operatory logiczne:  
  
```  
int w, x, y, z;  
  
if ( x < y && y < z )  
    printf( "x is less than z\n" );  
```  
  
 W tym przykładzie `printf` funkcja jest wywoływana, aby wydrukować komunikat, jeśli `x` jest mniejsza niż `y` i `y` jest mniejsza niż `z`. Jeśli `x` jest większa niż `y`, drugi argument operacji (`y < z`) nie jest obliczane i nic nie jest wydrukowane. Należy pamiętać, że może to spowodować problemy w przypadku, gdy drugi argument operacji ma efekty uboczne, które są opiera się innego powodu.  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 W tym przykładzie Jeśli `x` jest równa albo `w`, `y`, lub `z`, drugi argument `printf` funkcja zwraca wartość true, a wartość 1 jest drukowana. W przeciwnym razie jest spełniony, drukowana wartość 0. Gdy tylko jeden z warunków zwraca wartość true, wygasa oceny.  
  
## <a name="see-also"></a>Zobacz też  
 [Operator logiczny AND: & &](../cpp/logical-and-operator-amp-amp.md)   
 [Logiczny OR Operator:&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)