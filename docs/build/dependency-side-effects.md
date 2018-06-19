---
title: Skutki uboczne zależności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7537e077a43318a487163d014b49d52cef66ce19
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367527"
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
 [Docelowe elementy](../build/targets.md)