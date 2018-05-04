---
title: Typy całkowite | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acc3dc7631602e8accd9574bf707798dae5ba0d9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="integer-types"></a>Typy całkowite
Każda stała całkowita posiada typ zależny od jej wartości i sposobu wyrażenia. Możesz wymusić żadnych stała całkowita na typ **długi** przez dołączenie literę **l** lub **L** na końcu stała; Aby wymusić na typ `unsigned` przez dodanie **u** lub **U** wartości. Małe litery **l** można pomylić z cyfrą 1 i należy unikać. Niektóre rodzaje **długi** wykonaj stałe całkowite:  
  
```  
/* Long decimal constants */  
10L  
79L  
  
/* Long octal constants */  
012L  
0115L  
  
/* Long hexadecimal constants */  
0xaL or 0xAL  
0X4fL or 0x4FL  
  
/* Unsigned long decimal constant */  
776745UL  
778866LU  
```  
  
 Typ przypisany do stałej zależy od wartości reprezentowanej przez stałą. Stała wartość musi być w zakresie reprezentowanych wartości dla tego typu. Określa typ stałej konwersje, które są wykonywane, gdy stała jest używany w wyrażeniu lub znak minus (**-**) są stosowane. Ta lista zawiera podsumowanie reguł konwersji dla stałych całkowitych.  
  
-   Jest typem stałą dziesiętną bez sufiksu `int`, **długi int**, lub **unsigned int długi**. Pierwszy z tych trzech typów, w którym wartość stałej może być reprezentowana jest typem przypisanym do stałej.  
  
-   Typ przypisane do ósemkowe i szesnastkowe stałe, bez sufiksów jest `int`, `unsigned int`, **długi int**, lub **unsigned int długi** w zależności od wielkości stałej.  
  
-   Typ przypisane do stałe z **u** lub **U** sufiks jest **unsigned int** lub **unsigned int długi** w zależności od ich rozmiaru.  
  
-   Typu przypisany do stałe z **l** lub **L** sufiks jest **długi int** lub **unsigned int długi** w zależności od ich rozmiaru.  
  
-   Typ przypisane do stałe z **u** lub **U** i **l** lub **L** sufiks jest **unsigned int długi**.  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe całkowite języka C](../c-language/c-integer-constants.md)