---
title: "Typy całkowite | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e324976d0054cd1b32188b6ebe0f10ab4e1bdd69
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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