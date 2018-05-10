---
title: 2.6.3 dyrektywa określająca bariery | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68df92207feb45a77055098cdb1227a68b04bcab
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="263-barrier-directive"></a>2.6.3 Dyrektywa określająca bariery
**Bariery** dyrektywy synchronizuje wszystkie wątki w zespole. W przypadku każdego wątku w zespole oczekuje, aż wszystkie pozostałe on osiągnąć tego punktu. Składnia **bariery** dyrektywy wygląda następująco:  
  
```  
#pragma omp barrier new-line  
```  
  
 Po wszystkie wątki w zespole wystąpił bariery, rozpoczyna się każdy wątek w zespole, wykonywania instrukcji po dyrektywie bariery równolegle. Należy pamiętać, że ponieważ **bariery** dyrektywy nie ma instrukcji języka C w ramach jego składni, istnieją pewne ograniczenia na jej położenie w programie. Zobacz [dodatku C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) dla formalnego gramatyki. W poniższym przykładzie przedstawiono te ograniczenia.  
  
```  
/* ERROR - The barrier directive cannot be the immediate  
*          substatement of an if statement  
*/  
if (x!=0)  
   #pragma omp barrier  
...  
  
/* OK - The barrier directive is enclosed in a  
*      compound statement.  
*/  
if (x!=0) {  
   #pragma omp barrier  
}  
```