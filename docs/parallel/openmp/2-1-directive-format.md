---
title: 2.1 Format dyrektywy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c3ff4e0078ffd086ce3b62d8927184188f0ebdd8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="21-directive-format"></a>2.1 Format dyrektywy
Składnia OpenMP — dyrektywa formalnie jest określona przez gramatyki w [dodatku C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)i nieformalnego w następujący sposób:  
  
```  
#pragma omp directive-name  [clause[ [,] clause]...] new-line  
```  
  
 Rozpoczyna się od każdej dyrektywy **#pragma omp**, aby uniknąć potencjalnych konfliktów z innymi dyrektywy pragma (z systemem innym niż OpenMP lub dostawcy rozszerzeń OpenMP) pod tą samą nazwą. W pozostałej części dyrektywa jest zgodna z konwencjami standardów C i C++ dla dyrektywy kompilatora. W szczególności białe może służyć przed i po  **#** , a czasami biały znak musi być używane do oddzielania słów w dyrektywie. Przetwarzanie wstępne tokenów po **#pragma omp** podlegają makro zastąpienia.  
  
 Dyrektywy jest rozróżniana wielkość liter. Kolejność, w którym klauzul w dyrektywach nie ma znaczenia. Klauzule na dyrektywy może się powtarzać, w razie potrzeby, zgodnie z ograniczeniami wymienionymi w opisie każdej klauzuli. Jeśli *zmiennej listy* pojawia się w klauzuli, należy określić tylko zmienne. Tylko jeden *nazwy dyrektywy* może być określona dla dyrektywy.  Na przykład następujące dyrektywa jest niedozwolona:  
  
```  
/* ERROR - multiple directive names not allowed */  
#pragma omp parallel barrier  
```  
  
 OpenMP — dyrektywa dotyczy co najwyżej jeden następne instrukcja, która musi być strukturalnego bloku.