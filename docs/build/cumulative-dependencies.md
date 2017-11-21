---
title: "Zależności zbiorcze | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dependencies, cumulative
- cumulative dependencies in NMAKE
- dependencies
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f2fd356ae37eda8820e3a6e0e31a8cecde8d3929
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cumulative-dependencies"></a>Zależności zbiorcze
Zależności kumulują się w bloku opis, jeśli element docelowy jest powtarzany.  
  
 Na przykład to ustawienie zasad,  
  
```Output  
bounce.exe : jump.obj  
bounce.exe : up.obj  
   echo Building bounce.exe...  
```  
  
 jest szacowana jako to:  
  
```Output  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
```  
  
 Wiele obiektów docelowych w wielu wierszach zależności w bloku jeden opis są oceniane tak, jakby każdego zostały określone w bloku oddzielne opis, ale obiektów docelowych, które nie znajdują się w ostatnim wierszu zależności nie należy używać poleceń bloku. NMAKE próbuje użyć reguły wnioskowania dla tych celów.  
  
 Na przykład to ustawienie zasad,  
  
```Output  
leap.exe bounce.exe : jump.obj  
bounce.exe climb.exe : up.obj  
   echo Building bounce.exe...  
```  
  
 jest szacowana jako to:  
  
```Output  
  
leap.exe : jump.obj  
# invokes an inference rule  
bounce.exe : jump.obj up.obj  
   echo Building bounce.exe...  
climb.exe : up.obj  
   echo Building bounce.exe...  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty docelowe](../build/targets.md)