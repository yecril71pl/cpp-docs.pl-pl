---
title: 2.1 Format dyrektywy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1eec5a2f0e91df6e8d71797199bd3a3911a3aab0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="21-directive-format"></a>2.1 Format dyrektywy
Składnia OpenMP — dyrektywa formalnie jest określona przez gramatyki w [dodatku C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)i nieformalnego w następujący sposób:  
  
```  
#pragma omp directive-name  [clause[ [,] clause]...] new-line  
```  
  
 Rozpoczyna się od każdej dyrektywy **#pragma omp**, aby uniknąć potencjalnych konfliktów z innymi dyrektywy pragma (z systemem innym niż OpenMP lub dostawcy rozszerzeń OpenMP) pod tą samą nazwą. W pozostałej części dyrektywa jest zgodna z konwencjami standardów C i C++ dla dyrektywy kompilatora. W szczególności białe może służyć przed i po **#**, a czasami biały znak musi być używane do oddzielania słów w dyrektywie. Przetwarzanie wstępne tokenów po **#pragma omp** podlegają makro zastąpienia.  
  
 Dyrektywy jest rozróżniana wielkość liter. Kolejność, w którym klauzul w dyrektywach nie ma znaczenia. Klauzule na dyrektywy może się powtarzać, w razie potrzeby, zgodnie z ograniczeniami wymienionymi w opisie każdej klauzuli. Jeśli *zmiennej listy* pojawia się w klauzuli, należy określić tylko zmienne. Tylko jeden *nazwy dyrektywy* może być określona dla dyrektywy.  Na przykład następujące dyrektywa jest niedozwolona:  
  
```  
/* ERROR - multiple directive names not allowed */  
#pragma omp parallel barrier  
```  
  
 OpenMP — dyrektywa dotyczy co najwyżej jeden następne instrukcja, która musi być strukturalnego bloku.