---
title: "Skutki uboczne zależności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9d19426a34620cfdd14b426b94757715ca2d1cbd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="dependency-side-effects"></a>Skutki uboczne zależności
Jeśli określono element docelowy z dwukropkiem (:) w dwóch wierszach zależności w różnych lokalizacjach, a polecenia są wyświetlane po tylko jednego z wierszy, NMAKE interpretuje zależności tak, jakby sąsiadujących lub połączone. Nie jest wywoływany reguła wnioskowania dla zależności, która ma żadnych poleceń, ale zamiast tego założono, że zależności należą do bloku jeden opis i wykonuje polecenia określony za pomocą innych zależności. Na przykład to zbiór reguł:  
  
```Output  
bounce.exe : jump.obj  
   echo Building bounce.exe...  
  
bounce.exe : up.obj  
```  
  
 jest szacowana jako to:  
  
```Output  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
```  
  
 W tym celu nie występuje w przypadku podwójny dwukropek (`::`) jest używany. Na przykład to zbiór reguł:  
  
```Output  
bounce.exe :: jump.obj  
   echo Building bounce.exe...  
  
bounce.exe :: up.obj  
```  
  
 jest szacowana jako to:  
  
```Output  
bounce.exe : jump.obj  
   echo Building bounce.exe...  
  
bounce.exe : up.obj  
# invokes an inference rule  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty docelowe](../build/targets.md)