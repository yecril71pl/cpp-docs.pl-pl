---
title: wartość logiczna (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
dev_langs:
- C++
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2af648b2b93d2d01eaf66f5b642b6514063577d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410866"
---
# <a name="bool-c"></a>bool (C++)

To słowo kluczowe jest typu wbudowanego. Zmienna tego typu może mieć wartości [true](../cpp/true-cpp.md) i [false](../cpp/false-cpp.md). Wyrażenia warunkowe ma typ `bool` , więc wartości typu `bool`. Na przykład `i!=0` ma teraz **true** lub **false** w zależności od wartości `i`.  

**Visual Studio 2017 wersji 15.3 i nowszych** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): argument przyrostek lub prefiks inkrementacji lub dekrementacji operator nie może być typu **bool**. Innymi słowy, podane zmiennej **b** typu **bool**, wyrażenia te nie są już dozwolone:

```cpp
    b++;
    ++b;
    b--;
    --b;
```
  
Wartości **true** i **false** ma następującej relacji:  
  
```cpp  
!false == true  
!true == false  
```  
  
W poniższej instrukcji:  
  
```cpp  
if (condexpr1) statement1;   
```  
  
Jeśli `condexpr1` jest **true**, `statement1` jest zawsze wykonywane; Jeśli `condexpr1` jest **false**, `statement1` nie został wykonany.  
  
Operatory przyrostka lub prefiks **++** operator jest stosowany do zmiennej typu **bool**, zmienna ma ustawioną **true**. 
**Visual Studio 2017 wersji 15.3 i nowszych**: operator ++ dla **bool** została usunięta z języka i nie jest już obsługiwana.

Operatory przyrostka lub prefiks **--** do zmiennej tego typu nie można zastosować operatora.  
  
 **Bool** typ uczestniczy w promocje typów całkowitych. R typu **bool** można przekonwertować typu r **int**, z **false** staje się zero i **true** która staje się jeden. Jako typu różne **bool** uczestniczy w Rozpoznanie przeciążenia.  
  
## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Typy podstawowe](../cpp/fundamental-types-cpp.md)<br/>
