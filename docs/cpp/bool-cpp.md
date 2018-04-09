---
title: wartość logiczna (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
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
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2d5a8a86cfcc64b70e4910079461513c34fc7d0d
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2018
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
