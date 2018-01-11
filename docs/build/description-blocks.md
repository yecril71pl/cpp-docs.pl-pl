---
title: "Bloki opisów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 37f095f5ae46e4b555f1d3f7996bd5f357e58ee2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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