---
title: Bloki opisów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0784f08c479a8c8f3968ef61a01431cd9e0ca71e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="description-blocks"></a>Bloki opisów
Blok opis znajduje się w wierszu zależności opcjonalnie umieszczając za blok poleceń:  
  
```  
targets... : dependents...  
    commands...  
```  
  
 Wiersz zależności określa jeden lub więcej elementów docelowych i zero lub więcej elementów zależnych. Element docelowy musi być na początku wiersza. Oddzielne elementów docelowych z zależności dwukropkiem (:); spacji lub karty są dozwolone. Podział wiersza, należy użyć ukośnik odwrotny (\) po docelowej lub zależnym od. Jeśli element docelowy nie istnieje, ma wcześniejszą sygnatury czasowej niż zależną lub jest [pseudotarget](../build/pseudotargets.md), NMAKE wykonuje polecenia. Jeśli zależną jest celem odrębnie i nie istnieje lub jest nieaktualny w stosunku do jego własnej zależności, NMAKE aktualizuje zależnego przed zaktualizowaniem bieżącego zależności.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
 [Docelowe elementy](../build/targets.md)  
  
 [Zależności](../build/dependents.md)  
  
## <a name="see-also"></a>Zobacz też  
 [NMAKE — dokumentacja](../build/nmake-reference.md)